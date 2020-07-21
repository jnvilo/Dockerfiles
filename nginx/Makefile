.PHONY: build
REGISTRY_URL=hub.lnxsystems.com
PROJECT=library
IMAGE_NAME=nginx
TAG=1.0.0

.PHONY: build  all run 

all:  build tag push

build:
	docker build -t ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} .

pull:   
	docker  pull ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest 

tag: 
	docker tag ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
 
exec: build 
 	docker run --rm  -it ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest

push:  
	docker push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
	docker push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG}


