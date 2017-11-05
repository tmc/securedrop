TAG ?= $(shell git rev-parse HEAD)
IMAGE = securedrop-testinfra

.PHONY: images
images:
	docker build -t $(IMAGE)-test:$(TAG) .

.PHONY: test
test:
	docker run --privileged \
		-e COMMIT_SHA=$(TAG) \
		$(EXTRA_TEST_ARGS) \
		--name $(IMAGE)-test \
		-ti $(IMAGE)-test:$(TAG) \
		./test

.PHONY: testclean
testclean:
	docker rm -f $(IMAGE)-test
