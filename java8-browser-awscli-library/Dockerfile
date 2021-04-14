FROM openjdk:8-jdk-slim
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      git \
      openssh-client \
      procps \
      ca-certificates \
      curl \
      unzip \
      gnupg \
## Install aws cli v2
  && curl -sS "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
  && unzip -q awscliv2.zip \
  && rm awscliv2.zip \
  && ./aws/install \
## Install google chrome stable  
  && curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
  && sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' \
  && apt-get update \
  && apt install google-chrome-stable -y --no-install-recommends \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

# chrome driver のインストール
RUN CHROME_DRIVER_VERSION=$(curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE_89) \
 && echo "CHROME_DRIVER_VERSION: ${CHROME_DRIVER_VERSION}" \
 && curl -sS http://chromedriver.storage.googleapis.com/${CHROME_DRIVER_VERSION}/chromedriver_linux64.zip -o chromedriver_linux64.zip \
 && unzip -q chromedriver_linux64.zip \
 && rm chromedriver_linux64.zip \
 && mv -f ./chromedriver /usr/bin/chromedriver
