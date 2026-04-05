FROM alpine:latest

# Установка зависимостей
RUN apk add --no-cache ca-certificates bash libc6-compat gcompat wget

# Создаем рабочую папку
WORKDIR /app

# Скачиваем ОФИЦИАЛЬНЫЙ бинарник напрямую (версия 1.18.3 для amd64)
RUN wget https://github.com \
    && gunzip mihomo-linux-amd64-v1.18.3.gz \
    && mv mihomo-linux-amd64-v1.18.3 mihomo \
    && chmod +x mihomo

# Копируем скрипт запуска и дефолтный конфиг из вашего репозитория
COPY start-mihomo.sh /app/start-mihomo.sh
COPY mihomo-default.yaml /app/mihomo-default.yaml
RUN chmod +x /app/start-mihomo.sh

CMD ["/app/start-mihomo.sh"]
