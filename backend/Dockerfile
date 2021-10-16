FROM python:3.9-slim-bullseye

WORKDIR app
RUN pip install poetry

COPY src/pyproject.toml src/poetry.lock ./
RUN poetry install

COPY /src .

EXPOSE 8000
ENTRYPOINT poetry run alembic upgrade head && \
 poetry run python -m db.seeding && \
 poetry run uvicorn app:create_app --factory --host 0.0.0.0 --port 8000
