FROM ubuntu:15.10

MAINTAINER HyanCat <hyancat@live.cn>

# ADD sources.list    /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y iptables pptpd \
    && rm -rf /var/lib/apt/lists/*

COPY conf/pptpd.conf    /etc/
COPY conf/chap-secrets  /etc/ppp/
COPY conf/pptpd-options /etc/ppp/

EXPOSE 1723

CMD iptables -t nat -A POSTROUTING -s 10.99.99.0/24 -o eth0 -j MASQUERADE \
    && iptables -A FORWARD -s 10.99.99.0/24 -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j TCPMSS --set-mss 1356 \
    && pptpd --fg