FROM python:3.10-slim

WORKDIR /app

# зависимости psycopg2
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql-client \
    libpq-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# spaCy модели для русского языка
RUN pip install --no-cache-dir "spacy>=3.0.0" && \
    python -m spacy download ru_core_news_md

# установка зависимостей проекта
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "-m", "app.main"]