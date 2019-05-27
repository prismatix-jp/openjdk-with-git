FROM openjdk:9-jdk-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    procps \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*
    
