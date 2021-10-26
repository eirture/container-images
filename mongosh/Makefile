
version ?= 1.1.0
IMAGE_NAME=eirture/mongosh

.PHONY: build
build:
	docker build --build-arg=VERSION=${version} . -t ${IMAGE_NAME}:latest -t ${IMAGE_NAME}:${version}

