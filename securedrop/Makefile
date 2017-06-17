TAG ?= $(shell git rev-parse HEAD)
IMAGE = securedrop

.PHONY: images
images:
	docker build -t $(IMAGE):$(TAG) .
	cat Dockerfile Dockerfile.test | docker build -f - -t $(IMAGE)-test:$(TAG) .

.PHONY: test
test:
	docker run -ti $(IMAGE)-test:$(TAG) pytest -vvvv -x

.PHONY: test-config
test-config:
	source_secret_key=$(shell head -c 32 /dev/urandom | base64) \
	journalist_secret_key=$(shell head -c 32 /dev/urandom | base64) \
	scrypt_id_pepper=$(shell head -c 32 /dev/urandom | base64) \
	scrypt_gpg_pepper=$(shell head -c 32 /dev/urandom | base64) \
					  python -c 'import os; from jinja2 import Environment, FileSystemLoader; env = Environment(loader=FileSystemLoader(".")); env.get_template("config.py.example"); open("config.py", "w").write(env.get_template("config.py.example").render(dict((k, {"stdout":v}) for k,v in os.environ.iteritems())))'
