FROM debian:buster

RUN apt update \
    && apt upgrade -y \
    && apt -y install curl software-properties-common locales git \
    && apt -y install zip unzip \
    && apt -y install apt-transport-https \
    && apt -y install lzma liblzma-dev libcurl4 libcurl4-openssl-dev \
    && apt -y install make \
    && apt -y install build-essential \
    && apt -y install wget \ 
    && apt -y install curl \
    && apt -y install libtool \
    && apt -y install qbittorrent-nox -y \
    && adduser container \
    && apt-get update 
    

# Grant sudo permissions to container user for commands
RUN apt-get update && \
    apt-get -y install sudo

# Ensure UTF-8
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Install basic software support
RUN apt-get update && \
    apt-get install -y software-properties-common
RUN mv /usr/bin/qbittorrent-nox /usr/bin/qbittorrent

COPY ./entrypoint.sh /entrypoint.sh
RUN wget -O /start.sh https://raw.githubusercontent.com/Luxxy-GF/Luxxy-Eggs/main/qbittorrent/start.sh

RUN chmod +x /start.sh

USER container
ENV  USER container
ENV  HOME /home/container

WORKDIR /home/container


CMD ["/bin/bash", "/entrypoint.sh"]
