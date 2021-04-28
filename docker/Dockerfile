FROM python:3.7.10

ENV PATH="/system/converter/:${PATH}"

ENV HOST="0.0.0.0"

ENV PORT=8000

WORKDIR /system

COPY ./ /system/

RUN apt update \
    && apt install -y --no-install-recommends \
        build-essential \
        python3-opencv \
    && pip3 install --upgrade --no-cache-dir pip setuptools wheel pipenv \
    && pipenv lock -r > requirements.txt \
    && pip3 --no-cache-dir install -r requirements.txt \
    && sed -i -e "1i #\! /usr/bin/env python3\n" converter/convert.py \
    && ln converter/convert.py converter/convert

VOLUME /system/system/user_date

ENTRYPOINT gunicorn --bind=$HOST:$PORT wsgi:app
