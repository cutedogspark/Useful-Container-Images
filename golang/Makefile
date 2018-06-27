BASE_IMAGE := golang
BASE_VERSION := 1.10.3-alpine
BUILD_IMAGE := garychen/golang
BUILD_VERSION := $(BASE_VERSION)

all: latest push-image

latest:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}" -f Dockerfile \
		--build-arg BASE_IMAGE=${BASE_IMAGE} \
		--build-arg BASE_VERSION=${BASE_VERSION} .

push-image:
	docker push $(BUILD_IMAGE):$(BUILD_VERSION)
