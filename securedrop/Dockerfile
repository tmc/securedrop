FROM ubuntu@sha256:30204139c6ab96ebd75d72f34db390f28c4decd5e563488b4e485bf979397b67

RUN apt-get update # 2017-11-04
RUN apt-get install -y \
	python-pip libpython2.7-dev libssl-dev secure-delete gnupg2 ruby redis-server
# refs securedrop/issues/1594
RUN gem install sass -v 3.4.23

WORKDIR /app

COPY requirements requirements
RUN pip install -r requirements/securedrop-requirements.txt

COPY static static
COPY sass sass
RUN sass --force --stop-on-error --update sass:static/css --style compressed

#skip-if-test
COPY . /app

EXPOSE 8080 8081
CMD ["./manage.py", "run"]
