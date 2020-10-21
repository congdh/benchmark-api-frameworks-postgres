# benchmark-api-frameworks-postgres
Benchmark peformance python api frameworks with postgres

Install `hey` benchmark tool

```shell script
brew install hey
```

## Start database
Start database by `docker-compose`

```shell script
docker-compose up -d db pgadmin
```

Migrate database using `alembic`

```shell script
poetry run alembic upgrade head
```

## Benchmark FastAPI Sqlalchemy app

Start app
```shell script
poetry run uvicorn fastapi_sqlalchemy.main:app
```

Benchmark now

```shell script
hey -n 100 -c 10 http://127.0.0.1:8000/users/
```
