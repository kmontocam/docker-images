# tagged as /rust/tectonic:0.15.0-bookworm
FROM rust:1.82-bookworm AS builder

ENV DEBIAN_FRONTEND=noninteractive

# https://tectonic-typesetting.github.io/book/latest/howto/build-tectonic/#third-party-dependencies
RUN apt update && apt install -y --no-install-recommends \
    fontconfig \
    libfreetype6-dev \
    libgraphite2-dev \
    libharfbuzz-dev \
    libicu-dev \
    libpng-dev \
    libssl-dev \
    zlib1g-dev \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

RUN cargo install tectonic --version 0.15.0 --features external-harfbuzz

FROM debian:bookworm-slim

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y --no-install-recommends \
    fontconfig \
    libfreetype6-dev \
    libgraphite2-dev \
    libharfbuzz-dev \
    libicu-dev \
    libpng-dev \
    libssl-dev \
    ca-certificates \
    zlib1g-dev \
    curl \
    && apt clean \
    && rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr/local/cargo/bin/tectonic /usr/local/bin/tectonic

LABEL maintainer="me@kmontocam.com" \
    description="rust image with tectonic for latex compilation"

ENTRYPOINT ["tectonic"]
