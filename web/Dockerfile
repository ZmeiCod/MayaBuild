FROM node:alpine as builder

WORKDIR /app
COPY package.json package-lock.json ./
RUN npm install --legacy-peer-deps
COPY . .
RUN npm run build

FROM nginx:stable-alpine

COPY --from=builder /app/build /usr/share/nginx/html/web
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000
CMD ["nginx", "-g", "daemon off;"]