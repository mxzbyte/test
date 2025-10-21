FROM python:3.12-alpine

# Install base dependencies
RUN apk add --no-cache curl build-base bash

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Add Poetry to PATH for all future layers
ENV PATH="/root/.local/bin:$PATH"

# Copy project files
WORKDIR /app
COPY pyproject.toml poetry.lock* ./

# Install dependencies
RUN poetry install --no-interaction --no-root

# Copy app
COPY . .


ENV PYTHONPATH=/app \
    DOMAIN=localhost \
    ENVIRONMENT=local \
    PROJECT_NAME="Full Stack FastAPI Project" \
    STACK_NAME=full-stack-fastapi-project \
    SECRET_KEY=changethis123 \
    FIRST_SUPERUSER=chanllenge@devopsdojo.com \
    FIRST_SUPERUSER_PASSWORD=devopsdojo57 \
    USERS_OPEN_REGISTRATION=True \
    EMAILS_FROM_EMAIL=info@example.com \
    SMTP_TLS=True \
    SMTP_SSL=False \
    SMTP_PORT=587  \
    POSTGRES_SERVER=localhost \
    POSTGRES_PORT=5432 \
    POSTGRES_DB=app \
    POSTGRES_USER=app \
    POSTGRES_PASSWORD=changethis123

EXPOSE 8000
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000", "--workers", "2"]
