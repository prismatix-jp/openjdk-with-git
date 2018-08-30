FROM openjdk:11-jdk-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    procps \
    && rm -rf /var/lib/apt/lists/*
