FROM python:3.6
MAINTAINER devexity

RUN mkdir /application

COPY . /application

WORKDIR /application

RUN pip install -r requirements.txt

RUN python3 setup.py install

CMD python3 tools/create_db.py
