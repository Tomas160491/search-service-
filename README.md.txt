# Search Service

Простой поисковик по текстам документов: FastAPI + PostgreSQL + Elasticsearch, всё в Docker.

## Запуск

```bash
docker compose up -d --build

# залить CSV
docker compose cp posts.csv app:/app/posts.csv
docker compose exec app python main.py load /app/posts.csv
```

## API

| Метод  | Путь                  | Описание |
|--------|-----------------------|----------|
| GET    | `/search?q=<текст>`   | Поиск, до 20 документов, сортировка по `created_date desc` |
| DELETE | `/documents/{id}`     | Удаление из БД и индекса |

Swagger: http://localhost:8000/docs

## Стек
- FastAPI (async)
- SQLAlchemy 2.0 + asyncpg
- Elasticsearch 8 (async client)
- Docker Compose