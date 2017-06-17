TAG ?= $(shell git rev-parse HEAD)
IMAGE = securedrop-testinfra

.PHONY: images
images:
	docker build -t $(IMAGE):$(TAG) .
