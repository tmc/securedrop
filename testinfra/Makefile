TAG ?= $(shell git describe --always --long --dirty)
IMAGE = securedrop-testinfra

images:
	docker build -t $(IMAGE):$(TAG) .
