FROM ubuntu:15.10

MAINTAINER HyanCat <hyancat@live.cn>

# ADD sources.list    /etc/apt/sources.list

RUN apt-get update && \
    apt-get install -y python-pip && \
    pip install shadowsocks && \
    apt-get purge -y python-pip python+ python-pkg-resources+ && \
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ENV SERVER_ADDR 0.0.0.0
ENV SERVER_PORT 9388
ENV PASSWORD	secret
ENV METHOD      aes-256-cfb
ENV TIMEOUT     300
ENV WORKERS     10

EXPOSE $SERVER_PORT

CMD ssserver -s $SERVER_ADDR \
             -p $SERVER_PORT \
             -k ${PASSWORD:-$(hostname)} \
             -m $METHOD \
             -t $TIMEOUT \
             --fast-open \
             --workers $WORKERS
