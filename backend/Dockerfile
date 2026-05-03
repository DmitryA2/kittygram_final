FROM python:3.9

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Сбор статики (в STATIC_ROOT = '/app/static/')
RUN python manage.py collectstatic --noinput

# Запуск gunicorn
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]