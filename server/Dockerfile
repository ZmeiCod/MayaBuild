FROM node:22.14.0

COPY package.json package-lock.json
RUN npm install
COPY . .
RUN npm run build

EXPOSE 5000
CMD ["node", "index.js"]
