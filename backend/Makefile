ARCH=amd64
IMG_TAG="login-backend:v1.0.0"
IMG_REGISTRY=180993267331.dkr.ecr.ap-northeast-2.amazonaws.com
REPO_NAME=anna-be
IMG_TAG=${IMG_REGISTRY}/${REPO_NAME}:login-test

all:
	cat ./Makefile

test:
	pnpm test

node:
	pnpm install 
	pnpm run build

image: node
	docker build --platform=linux/${ARCH} --tag ${IMG_TAG} .

push: image
	aws ecr get-login-password --region ap-northeast-2 | docker login --username AWS --password-stdin ${IMG_REGISTRY}
	docker push ${IMG_TAG}
