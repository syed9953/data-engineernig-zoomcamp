FROM python:3.13.12-slim
RUN apt-get update && apt-get install -y libpq5 && rm -rf /var/lib/apt/lists/*
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
WORKDIR /code
ENV PATH="/code/.venv/bin:$PATH"

COPY pyproject.toml uv.lock .python-version ./
RUN uv sync --locked
 

# COPY ingest_data.py .
COPY ingest_data_2.py .

ENTRYPOINT ["python", "ingest_data_2.py"]


