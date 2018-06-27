BUILD_IMAGE := garychen/kong
BUILD_VERSION := 0.13.1-alpine

all: latest push-image

latest:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:${BUILD_VERSION}" -f Dockerfile .

push-image:
	docker push $(BUILD_IMAGE):$(BUILD_VERSION)
