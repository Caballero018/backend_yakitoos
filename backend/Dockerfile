# Etapa de desarrollo
FROM python:3.12 AS dev
WORKDIR /usr/src/app
COPY backend/requirements-dev.txt .
RUN pip install -r requirements-dev.txt
COPY backend/ .
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

# Etapa de producción
FROM python:3.12-slim AS prod
WORKDIR /usr/src/app
COPY backend/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
CMD ["gunicorn", "myapp.wsgi:application", "--bind", "0.0.0.0:8000"]
