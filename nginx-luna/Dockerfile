FROM ccr.ccs.tencentyun.com/based-image/alpine:based

RUN mkdir /opt

WORKDIR /opt

ENV luna_version 1.5.2

RUN apk add --no-cache wget nginx \
    && cd /opt \
    && wget https://github.com/jumpserver/luna/releases/download/${luna_version}/luna.tar.gz -O /opt/luna.tar.gz \
    && tar zxf luna.tar.gz \
    && chown -R root:root luna  \
    && rm -rf /etc/nginx/conf.d/default.conf \
    && rm -rf /opt/luna.tar.gz

EXPOSE 80

CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
