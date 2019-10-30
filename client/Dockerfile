# 00 temp build stage -> dumped when done build -> won't be in image
FROM node:alpine as builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# 00 FROM will terminate block above
FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
# 00 nginx default cmd is to start server, so don't need to specify