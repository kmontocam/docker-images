# tagged as /rust/sqlx-cli-ssl:1.82-bookworm
FROM rust:1.82-bookworm

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y --no-install-recommends \
    libssl-dev \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

RUN cargo install sqlx-cli

LABEL maintainer="me@kmontocam.com" \
    description="rust image with sqlx-cli for database migrations and preparations"
