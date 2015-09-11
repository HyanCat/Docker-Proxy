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

RUN mkdir /root/log

EXPOSE 9388

CMD ssserver -c /etc/shadowsocks.json >> /root/log/shadowsocks.log 2>&1

