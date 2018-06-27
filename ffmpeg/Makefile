BASE_IMAGE := alpine
BASE_VERSION := 3.7
BUILD_IMAGE := garychen/ffmpeg
BUILD_VERSION := $(BASE_VERSION)

all: ffmpeg-3.3.2-vaapi ffmpeg-4.0.1 push-image-3.3.2-vaapi push-image-ffmpeg-4.0.1

ffmpeg-3.3.2-vaapi:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:3.3.2-vaapi" -f Dockerfile.FFMPEG-3.3.2-VAAPI .

push-image-3.3.2-vaapi:
	docker push $(BUILD_IMAGE):3.3.2-vaapi

ffmpeg-4.0.1:
	echo "Build images"
	docker build -t "${BUILD_IMAGE}:4.0.1" -f Dockerfile.FFMPEG-4.0.1 .

push-image-ffmpeg-4.0.1:
	docker push $(BUILD_IMAGE):4.0.1
