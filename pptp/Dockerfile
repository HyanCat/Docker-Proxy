FROM ubuntu:latest

MAINTAINER HyanCat <hyancat@live.cn>

# ADD sources.list    /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y iptables pptpd \
    && rm -rf /var/lib/apt/lists/*

COPY entrypoint.sh /entrypoint.sh
RUN chmod 0700 /entrypoint.sh

EXPOSE 1723

ENTRYPOINT ["/entrypoint.sh"]
CMD pptpd --fg