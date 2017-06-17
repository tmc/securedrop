TAG ?= $(shell git describe --always --long --dirty)
IMAGE = securedrop

images:
	docker build -t $(IMAGE):$(TAG) .
