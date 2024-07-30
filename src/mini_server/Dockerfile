FROM ubuntu:20.04

# Установка необходимых пакетов и очистка кэша apt-get
RUN apt-get update && apt-get install -y \
    gcc \
    libfcgi-dev \
    spawn-fcgi \
    nginx && \
    rm -rf /var/lib/apt/lists/*

# Копирование исходников и сборка сервера
COPY ./server.c /usr/local/bin/
RUN gcc /usr/local/bin/server.c -o /usr/local/bin/server -lfcgi

# Копирование конфигурационного файла nginx
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf

# Создание пользователя и группы
RUN groupadd -r appgroup && useradd -r -g appgroup appuser

# Создание необходимых директорий и установка прав доступа
RUN mkdir -p /var/lib/nginx /var/log/nginx && \
    chown -R appuser:appgroup /var/lib/nginx /var/log/nginx /usr/local/bin/server

# Смена пользователя
USER appuser

# Экспонирование порта
EXPOSE 8080

# Добавление HEALTHCHECK
HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 CMD curl -f http://localhost:8080 || exit 1

# Запуск сервера и nginx
CMD spawn-fcgi -p 8080 /usr/local/bin/server && nginx -g "daemon off;"