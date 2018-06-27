BASE_IMAGE := alpine
BASE_VERSION := 3.7
BUILD_IMAGE := garychen/alpine
BUILD_VERSION := $(BASE_VERSION)

all: latest push-image

latest:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}" -f Dockerfile \
		--build-arg BASE_IMAGE=${BASE_IMAGE} \
		--build-arg BASE_VERSION=${BASE_VERSION} .

push-image:
	docker push $(BUILD_IMAGE):$(BUILD_VERSION)

export:
	docker save garychen/dj2-live-x-alpine:3.7 | gzip > dj2-live-x-alpine.tgz