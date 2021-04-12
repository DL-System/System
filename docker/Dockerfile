FROM python:3.7-alpine

WORKDIR /system

COPY ./ /system/

RUN set -xe && \
    rm -rf /var/lib/apt/lists/* && \
    apk update && \
    apk add --no-cache linux-headers py3-pip && \
    apk add --no-cache --virtual .build-deps \
        build-base gcc cmake python3-dev \
        freetype-dev libpng-dev openssl-dev \
        postgresql-dev musl-dev openblas-dev gfortran && \
    pip3 install --upgrade pip setuptools wheel numpy==1.16.4 && \
    pip3 --no-cache-dir install -r requirements.txt && \
    apk del .build-deps && \
    sed -i -e "1i #\!/usr/bin/python\n" converter/convert.py && \
    ln -s converter/convert.py /usr/bin/convert

ENTRYPOINT gunicorn wsgi:app
