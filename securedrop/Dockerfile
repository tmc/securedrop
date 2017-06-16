FROM ubuntu@sha256:30204139c6ab96ebd75d72f34db390f28c4decd5e563488b4e485bf979397b67

RUN apt-get update # 2017-06-15
RUN apt-get install -y \
	python-pip libpython2.7-dev libssl-dev secure-delete # for srm binary gnupg2 ruby
RUN gem install sass -v 3.4.23 # refs securedrop/issues/1594

WORKDIR /app

COPY requirements/securedrop-requirements.txt requirements/securedrop-requirements.txt
RUN pip install -r requirements/securedrop-requirements.txt

COPY . /app

EXPOSE 8080 8081
CMD ['./manage.py','run']
