FROM ubuntu@sha256:30204139c6ab96ebd75d72f34db390f28c4decd5e563488b4e485bf979397b67

RUN apt-get update # 2017-06-15
RUN apt-get install -y \
	make git curl python-pip libffi-dev libssl-dev libyaml-dev libpython2.7-dev

WORKDIR /build

COPY . /build/testinfra

RUN pip install -r requirements.txt
RUN ./test.py build
RUN ./test.py apptestclient
