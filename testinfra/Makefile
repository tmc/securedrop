TAG ?= $(shell git rev-parse HEAD)
IMAGE = securedrop-testinfra

images:
	docker build -t $(IMAGE):$(TAG) .
