FROM python:3.11-slim

WORKDIR /app

RUN pip install --upgrade pip && \
    pip install poetry

COPY pyproject.toml poetry.lock* /app/

RUN poetry install --no-root 

COPY . /app

# Указываем переменные окружения
ENV WORKERS=4

# Кманды для запуска FastAPI
CMD ["sh", "-c", "poetry run uvicorn main:app --host 0.0.0.0 --port 80 --workers $WORKERS"]