FROM openjdk:8-jdk-slim

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      git \
      openssh-client \
      procps \
      ca-certificates \
      curl \
      unzip \
      gnupg

# chrome driver のインストール
RUN CHROME_LATEST_VERSION=$(curl -sS omahaproxy.appspot.com/linux?channel=stable) \
 && echo "CHROME_LATEST_VERSION: ${CHROME_LATEST_VERSION}" \
 && CHROME_LATEST_MAJOR_VERSION=$(echo $CHROME_LATEST_VERSION | cut -d . -f 1) \
 && CHROME_DRIVER_VERSION=$(curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE_$CHROME_LATEST_MAJOR_VERSION) \
 && echo "CHROME_DRIVER_VERSION: ${CHROME_DRIVER_VERSION}" \
 && curl -sS http://chromedriver.storage.googleapis.com/${CHROME_DRIVER_VERSION}/chromedriver_linux64.zip -o chromedriver_linux64.zip \
 && unzip chromedriver_linux64.zip \
 && rm chromedriver_linux64.zip \
 && mv -f ./chromedriver /usr/bin/chromedriver

# chrome のインストール
RUN curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
 && sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
 && apt-get update \
 && apt install -y --no-install-recommends google-chrome-stable

RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/*
