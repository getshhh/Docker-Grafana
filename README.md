## Описание проекта

Этот проект на основе Docker Compose включает в себя несколько сервисов для мониторинга и DNS-резолвинга. В проекте используются следующие компоненты:

- **CoreDNS**: DNS-сервер для управления доменными именами.
- **Prometheus**: Система мониторинга и сбора метрик.
- **Node Exporter**: Экспортёр метрик для мониторинга серверов.
- **Grafana**: Платформа для визуализации данных и построения графиков.

## Структура проекта


## Используемые технологии

- **Docker**: Для контейнеризации приложений.
- **Docker Compose**: Для управления многоконтейнерными приложениями.

## Запуск проекта

1. Убедитесь, что у вас установлен Docker и Docker Compose.
2. Склонируйте репозиторий или загрузите файлы проекта.
3. Перейдите в директорию с файлом `docker-compose.yaml`.
4. Выполните команду:

   ```bash
   docker-compose up -d

## Порты

| Сервис       | Порт (хост) | Порт (контейнер) |
|--------------|-------------|-------------------|
| CoreDNS      | 5053        | 53                |
| Prometheus   | 9090        | 9090              |
| Node Exporter| 9100        | 9100              |
| Grafana      | 3000        | 3000              |


#CoreDNS

. {
    log
    errors
    auto
    reload 10s
    forward . 1.1.1.1:53
    hosts /etc/coredns/sosa.com.hosts sosa.com
}


#Prometheus

global:
  scrape_interval: 15s
scrape_configs:
  - job_name: prometheus
    static_configs:
      - targets: ['localhost:9090']
  - job_name: node
    static_configs:
      - targets: ['node-exporter:9100']

#Grafana

apiVersion: 1

providers:
  - name: Default 
    folder: Services 
    type: file
    options:
      path: /var/lib/grafana/dashboards

#Завершение работы


```bash
   docker-compose down
