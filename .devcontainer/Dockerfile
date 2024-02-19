FROM python:3.11-slim

# Install system dependencies
ENV TZ=Asia/Tokyo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update\
    && apt-get install -y --no-install-recommends \
        openssh-server \
        vim \
        curl \
        wget \
        git \
        zip \
        tcptraceroute \
        net-tools \
        dnsutils \
        tcpdump \
        iproute2 \
        nano \
        cron \
        libgomp1 \
        build-essential \
    && pip install --upgrade pip 

# Install python dependencies
COPY requirements.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt

# Add user
ARG UID=1000
ARG GID=1000
RUN groupadd -g $GID dev \
    && useradd -m -u $UID -g $GID dev

USER dev

