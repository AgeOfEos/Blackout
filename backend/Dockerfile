FROM python:3.12-alpine

WORKDIR /backend

COPY pyproject.toml poetry.lock ./

RUN apk add --no-cache --virtual .build-deps gcc musl-dev \
    && pip install poetry \
    && poetry config virtualenvs.create false \
    && poetry install --no-dev --extras bjoern \
    && apk del .build-deps

COPY . .

EXPOSE 80

CMD ["python", "run.py", "0.0.0.0", "80"]