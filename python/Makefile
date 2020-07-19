.PHONY: build
REGISTRY_URL=hub.lnxsystems.com
PROJECT=library
IMAGE_NAME=python
TAG=centos8

.PHONY: build  all

all:  build tag push

build:
	podman build -t ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} .

pull:   
	podman  pull ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest 

tag: 
	podman tag ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
 
push:  build
	podman push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
	podman push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG}
