FROM ccr.ccs.tencentyun.com/based-image/pyenv:based

ENV jumpserver_version=1.5.2

RUN cd /opt \
    && source /opt/py3/bin/activate \
    && apk add --no-cache gcc g++ make automake git libgss krb5-libs libjpeg sshpass mysql-dev openldap-dev openssh-client \
    && apk add --no-cache glib-dev krb5-dev zlib-dev freetype-dev tiff-dev libzip-dev lcms2-dev tcl-dev libwebp-dev tk-dev libffi-dev \
    && git clone -b ${jumpserver_version} https://github.com/jumpserver/jumpserver.git \
    && pip install -r /opt/jumpserver/requirements/requirements.txt \
    && apk del gcc g++ make automake

COPY entrypoint.sh /

COPY config.py /opt/jumpserver/config.py

RUN chmod +x /entrypoint.sh

VOLUME /opt/jumpserver/data

EXPOSE 8080

ENTRYPOINT ["/entrypoint.sh"]
