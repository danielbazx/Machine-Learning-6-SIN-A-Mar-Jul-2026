FROM python:3.12-slim

RUN apt-get update && apt-get install -y \
    curl \
    git \
    git-lfs \
    && rm -rf /var/lib/apt/lists/*

RUN git lfs install --system

RUN curl -LsSf https://astral.sh/uv/install.sh | sh

ENV PATH="/root/.local/bin:$PATH" 

RUN uv --version

WORKDIR /app

RUN uv venv .danielenv

COPY requirements.txt .

# CORRECCIÓN AQUÍ: Cambiado de .venv/python a .venv/bin/python
RUN uv pip install --python .danielenv/bin/python -r requirements.txt

ENV VIRTUAL_ENV=/app/.danielenv
ENV PATH="/app/.venv/bin:$PATH"