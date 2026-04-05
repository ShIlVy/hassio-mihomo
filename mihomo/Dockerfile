FROM alpine:latest

# Устанавливаем зависимости и создаем ССЫЛКУ на загрузчик
RUN apk add --no-cache ca-certificates bash libc6-compat gcompat \
    && mkdir -p /lib64 \
    && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2

WORKDIR /app

# Копируем файл из вашего репозитория (тот, что 44 МБ)
COPY mihomo/mihomo-amd64 /app/mihomo
COPY start-mihomo.sh /app/start-mihomo.sh
COPY mihomo-default.yaml /app/mihomo-default.yaml

# Даем права на запуск
RUN chmod +x /app/mihomo /app/start-mihomo.sh

CMD ["/app/start-mihomo.sh"]
