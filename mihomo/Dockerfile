# Используем Debian Bullseye (slim версия для экономии места)
# В нем есть все необходимые библиотеки glibc для вашего процессора N3350
FROM debian:bullseye-slim

# Установка базовых системных пакетов
RUN apt-get update && apt-get install -y \
    ca-certificates \
    bash \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Создаем рабочую директорию приложения
WORKDIR /app

# Копируем бинарник и скрипты из вашего репозитория.
# ВНИМАНИЕ: Если файл mihomo-amd64 лежит в КОРНЕ репозитория, уберите "mihomo/" в начале пути ниже.
# Если он лежит внутри папки mihomo, оставьте как есть.
COPY mihomo-amd64 /app/mihomo
COPY start-mihomo.sh /app/start-mihomo.sh
COPY mihomo-default.yaml /app/mihomo-default.yaml

# Даем права на исполнение бинарнику и скрипту запуска
RUN chmod +x /app/mihomo /app/start-mihomo.sh

# Эта команда запустит ваш исправленный скрипт, который мы обсуждали ранее
CMD ["/app/start-mihomo.sh"]
