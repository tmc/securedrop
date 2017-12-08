# ubuntu:14.04 as of 2017-11-15
FROM ubuntu@sha256:f6eed4def93a3b54da920737f0abf1a8cae2e480bb368280c898265fcaf910a3
RUN apt-get install -y \
	python-pip libpython2.7-dev libssl-dev secure-delete gnupg2 ruby redis-server
RUN apt-get install -y xvfb

WORKDIR /testinfra

COPY requirements.txt /testinfra

RUN pip install -r requirements.txt


COPY . /testinfra
