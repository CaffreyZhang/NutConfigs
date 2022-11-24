FROM ubuntu:latest

COPY execsnoop /usr/bin/execsnoop

RUN sed -i "s@http://.*archive.ubuntu.com@https://mirrors.tuna.tsinghua.edu.cn@g" /etc/apt/sources.list && \
    sed -i "s@http://.*security.ubuntu.com@https://mirrors.tuna.tsinghua.edu.cn@g" /etc/apt/sources.list

RUN apt update && \
    apt install -y sysstat dstat linux-tools-common linux-tools-generic linux-tools-`uname -r` && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*
