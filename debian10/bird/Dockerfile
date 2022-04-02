FROM kathara/base:debian10

ARG DEBIAN_FRONTEND="noninteractive"
RUN echo "deb http://ftp.debian.org/debian buster-backports main" > /etc/apt/sources.list.d/backports.list && \
	apt update && apt full-upgrade -y
RUN apt remove -y bird;apt autoremove -y && apt install -y -t buster-backports bird2

COPY local.conf /etc/sysctl.d/local.conf

RUN apt clean && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*
