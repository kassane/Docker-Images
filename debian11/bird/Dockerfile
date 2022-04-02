FROM kathara/base:debian11

ARG DEBIAN_FRONTEND="noninteractive"
RUN apt update && apt full-upgrade -y
RUN apt install -y bird iptables

COPY local.conf /etc/sysctl.d/local.conf
RUN sysctl --system

RUN apt clean && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*
