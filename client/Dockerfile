FROM  node:20-alpine3.17 AS builder
WORKDIR /app
COPY package.json .
RUN npm install --force --silent
COPY . .
RUN npm run build
FROM nginx:1.25.2-alpine-slim
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80 
CMD ["nginx", "-g", "daemon off;"]