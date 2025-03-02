# Первый этап: сборка приложения на Node.js
FROM node:alpine AS build

# Установка рабочего каталога
WORKDIR /app

# Копируем необходимые файлы для установки зависимостей
COPY package.json package-lock.json ./
RUN npm install

# Копируем остальные файлы приложения
COPY . .

# Собираем приложение, если есть сборка
RUN npm run build

# Второй этап: настройка Nginx с приложением
FROM nginx:stable-alpine

# Копируем собранные файлы в Nginx
COPY --from=build /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Устанавливаем и запускаем Node.js приложение
# Здесь вы можете использовать другую директорию, если необходимо
COPY --from=build /app /app
WORKDIR /app

# Установка npm-пакетов для работы Node.js приложения
RUN npm install --production

# Устанавливаем переменную окружения для работы приложения
ENV NODE_ENV=production

# Параметры для запуска Node.js сервера
EXPOSE 5000
CMD ["node", "server.js"]
