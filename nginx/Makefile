BUILD_IMAGE := garychen/nginx
BUILD_VERSION := 1.1.0

CONTAINER_NAME = nginx
WEB_PORT = 88

all: alpine alpine-qeek alpine-qeek-ffmpeg push-image-alpine push-image-alpine-qeek push-image-alpine-qeek-ffmpeg

alpine:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}-alpine" -f Dockerfile.alpine .

alpine-run:
	docker run -d --rm -p ${WEB_PORT}:80 --name ${CONTAINER_NAME} ${BUILD_IMAGE}:${BUILD_VERSION}-alpine

push-image-alpine:
	docker push ${BUILD_IMAGE}:${BUILD_VERSION}-alpine

alpine-qeek:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek" -f Dockerfile.alpine_qeek .

alpine-qeek-run:
	docker run -d --rm -p ${WEB_PORT}:80 --name ${CONTAINER_NAME} ${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek

push-image-alpine-qeek:
	docker push ${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek

alpine-qeek-ffmpeg:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek-ffmpeg" -f Dockerfile.alpine_qeek_ffmpeg .

alpine-qeek-ffmpeg-run:
	docker run -d --rm -p ${WEB_PORT}:80 --name ${CONTAINER_NAME} ${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek-ffmpeg

push-image-alpine-qeek-ffmpeg:
	docker push ${BUILD_IMAGE}:${BUILD_VERSION}-alpine-qeek-ffmpeg
