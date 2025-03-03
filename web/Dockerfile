FROM node:22 as builder

WORKDIR /var/lib/app/
COPY ./package.json ./
COPY ./package-lock.json ./
COPY ./src/ ./src
COPY ./public/ ./public

ARG PUBLIC_URL
RUN npm install --legacy-peer-deps
RUN npm run build

FROM nginx:latest

COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /var/lib/app/build/ /var/www/
