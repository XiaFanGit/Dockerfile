FROM ccr.ccs.tencentyun.com/based-image/pyenv:based

ENV coco_version=1.5.2

RUN wget https://github.com/jumpserver/coco/archive/${coco_version}.tar.gz -O /opt/coco.tar.gz \
    && cd /opt \
    && tar zxf coco.tar.gz \
    && ln -sv coco-${coco_version} coco \
    && rm -rf /opt/coco.tar.gz \
    && apk add --no-cache gcc g++ make automake linux-headers sshpass libffi-dev krb5-dev libressl-dev \
    && source /opt/py3/bin/activate \
    && pip install -r /opt/coco/requirements/requirements.txt \
    && apk del gcc g++ make automake

WORKDIR /opt/coco

EXPOSE 2222 5000

RUN echo > config.yml

CMD source /opt/py3/bin/activate && cd /opt/coco && python ./run_server.py
