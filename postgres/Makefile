BUILD_IMAGE := garychen/postgres

all: alpine-9.5 alpine-10 push-image-alpine-9.5 push-image-alpine-10

alpine-9.5:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:alpine-9.5" -f 9.5/Dockerfile ./9.5

push-image-alpine-9.5:
	docker push ${BUILD_IMAGE}:alpine-9.5

alpine-10:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:alpine-10" -f 10/Dockerfile ./10

push-image-alpine-10:
	docker push ${BUILD_IMAGE}:alpine-10