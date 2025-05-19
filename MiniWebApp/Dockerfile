FROM python:alpine

WORKDIR /app

# Instalar dependencias necesarias para compilar mysqlclient
RUN apk add --no-cache \
    mariadb-dev \
    gcc \
    musl-dev \
    python3-dev \
    build-base \
    pkgconf

# Copiar los requerimientos e instalarlos
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copiar el código de la aplicación
COPY webapp/ .

# Establecer las variables de entorno
ENV FLASK_APP=run.py
ENV FLASK_DEBUG=0

# Exponer el puerto de la aplicación
EXPOSE 5000

# Comando para ejecutar la aplicación
CMD ["flask", "run", "--host=0.0.0.0"]