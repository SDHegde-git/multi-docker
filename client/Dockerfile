# we can provide custome name to build pahse using tag name
# using as <tag_name>
FROM node:alpine as builder
WORKDIR /app
COPY ./package.json .
RUN npm install
COPY . .
RUN npm run build

# build will generate the folders inside working directory (i.e WORKDIR here /app/build)

# here we can write one more build pahse of docker here, it include diff base image
FROM nginx
# this is for elasti bean AWS service, to expose port for outside access.
EXPOSE 3000
COPY ./nginx/default.conf  /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html