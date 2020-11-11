FROM openjdk:10-jdk-slim

RUN echo "deb http://ftp.us.debian.org/debian testing main" >> /etc/apt/sources.list \
    && apt-get clean && apt-get update && apt-get install -y --no-install-recommends \
    git \
    openssh-client \
    procps \
    ca-certificates \
    -o APT::Immediate-Configure=0 \
    && rm -rf /var/lib/apt/lists/*
