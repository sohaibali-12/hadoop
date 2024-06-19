OWN_DIR := $(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))
include $(OWN_DIR)/../Makefile.common
IMAGE_NAME := hadoop-build

$(info Directory is $(OWN_DIR))

.PHONY: docker
docker: build-image

.PHONY: build-image
build-image:
	docker build -t $(IMAGE_NAME) -f Dockerfile $(OWN_DIR)/../../../

.PHONY: build-image-no-cache
build-image-no-cache:
	docker build --no-cache -t -f Dockerfile $(OWN_DIR)/../../../


.PHONY: docker-publish
docker-publish: ecr-login docker docker-tag docker-push

.PHONY: docker-publish-jenkins
docker-publish-jenkins: docker-push-jenkins docker-clean