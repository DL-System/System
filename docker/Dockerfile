FROM python:3.7-slim-buster

WORKDIR /system

COPY ./ /system/

RUN apt update \
    && apt install -y --no-install-recommends \
        build-essential \
        python3-opencv \
    && pip3 install --upgrade pip setuptools wheel numpy==1.16.4 \
    && pip3 --no-cache-dir install -r requirements.txt \
    && sed -i -e "1i #\! /usr/bin/env python3\n" converter/convert.py \
    && ln converter/convert.py converter/convert

ENV PATH="/system/converter/:${PATH}"

ENV HOST="0.0.0.0"

ENV PORT=8000

VOLUME /system/system/user_date

ENTRYPOINT gunicorn --bind=$HOST:$PORT wsgi:app
