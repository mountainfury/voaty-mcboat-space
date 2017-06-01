FROM python:3.5
MAINTAINER devexity

RUN mkdir /application

COPY . /application

WORKDIR /application

RUN pip install -r requirements.txt

RUN python3 setup.py install

RUN python3 tools/create_db.py
