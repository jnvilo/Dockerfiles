.PHONY: build
REGISTRY_URL=hub.lnxsystems.com
PROJECT=library
IMAGE_NAME=terraform
TAG=1.0.1
TER_VER=0.12.29


.PHONY: build  all run 

all:  build tag 

build:
	docker build -t ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} .

pull:   
	docker  pull ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest 

tag: 
	docker tag ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG} ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
 
exec: build 
 	docker run --rm  -it ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest /bin/bash

push:  
	docker push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:latest
	docker push ${REGISTRY_URL}/${PROJECT}/${IMAGE_NAME}:${TAG}
	
terraform_${TER_VER}_linux_amd64.zip:
	wget https://releases.hashicorp.com/terraform/${TER_VER}/terraform_${TER_VER}_linux_amd64.zip
	rm -rf terraform

terraform: terraform_${TER_VER}_linux_amd64.zip
	unzip terraform_${TER_VER}_linux_amd64.zip


terraform-provider-upcloud: go
	git clone git@github.com:UpCloudLtd/terraform-provider-upcloud.git

go1.14.7.linux-amd64.tar.gz:
	wget https://golang.org/dl/go1.14.7.linux-amd64.tar.gz

go:  go1.14.7.linux-amd64.tar.gz
	tar -zxvf go1.14.7.linux-amd64.tar.gz

clean:
	rm -rf terraform-provider-upcloud
	rm -f terraform-*-zip
	rm -rf go
	rm -f go1.*.tar.gz
