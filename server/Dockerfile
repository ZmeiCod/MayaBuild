FROM node:alpine AS build

COPY package.json package-lock.json
RUN npm install
COPY . .
RUN npm run build

EXPOSE 5000
CMD ["node", "server.js"]
