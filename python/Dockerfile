FROM python:3.6-slim-stretch

COPY conf/sources.list /etc/apt/sources.list
COPY conf/pip.conf ~/.pip/pip.conf

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone

RUN apt-get update

CMD ["python3"]
