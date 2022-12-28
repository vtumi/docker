FROM node:19

RUN apt-get install -y wget \ 
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \ 
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list \
    && apt-get update && apt-get -y install google-chrome-stable chromium  xvfb\
    && rm -rf /var/lib/apt/lists/* \
    && echo "Chrome: " && google-chrome --version
WORKDIR /app
ENV WECHATY_PUPPET_WECHAT_ENDPOINT=/usr/bin/google-chrome
CMD xvfb-run --server-args="-screen 0 1024x768x24"
