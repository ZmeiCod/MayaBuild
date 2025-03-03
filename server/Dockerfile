FROM node:22.14.0

WORKDIR /server

COPY package.json ./
RUN npm install

COPY . .

RUN npm run

EXPOSE 5000
CMD ["node", "index.js"]
