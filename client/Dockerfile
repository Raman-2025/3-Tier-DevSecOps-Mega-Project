# production stage
FROM node:18-alpine AS BUILDER
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# serve by nginx
FROM nginx:alpine
COPY default.conf /etc/nginx/config.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]
