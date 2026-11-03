# syntax=docker/dockerfile:1

FROM python:3.8-slim-buster

RUN echo "deb http://mirrors.ustc.edu.cn/debian buster main contrib non-free" > /etc/apt/sources.list \
    && echo "deb http://mirrors.ustc.edu.cn/debian buster-updates main contrib non-free" >> /etc/apt/sources.list \
    && echo "deb http://mirrors.ustc.edu.cn/debian-security buster/updates main contrib non-free" >> /etc/apt/sources.list \
    && apt-get update --fix-missing \
    && apt-get install -y --no-install-recommends \
        libpq-dev \
        gcc \
        vim \
        apache2-utils \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
