FROM nginx:latest

# Копируем шаблон конфигурации Nginx
COPY nginx.conf.template /etc/nginx/nginx.conf.template

# Создаем директорию для Certbot challenge
RUN mkdir -p /var/www/certbot

# Копируем SSL сертификаты (изначально могут отсутствовать)
COPY ./ssl/cert.pem /etc/ssl/certs/cert.pem
COPY ./ssl/privkey.pem /etc/ssl/private/privkey.pem

# Заменяем переменные окружения на их значения и запускаем Nginx
CMD envsubst '${DOMAIN}' < /etc/nginx/nginx.conf.template > /etc/nginx/nginx.conf && nginx -g 'daemon off;'
