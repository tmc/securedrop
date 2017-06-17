TAG ?= $(shell git rev-parse HEAD)
IMAGE = securedrop

images:
	docker build -t $(IMAGE):$(TAG) .
	cat Dockerfile Dockerfile.test | docker build -f - -t $(IMAGE)-test:$(TAG) .

test:
	docker run -ti $(IMAGE)-test:$(TAG) pytest -vvvv -x
