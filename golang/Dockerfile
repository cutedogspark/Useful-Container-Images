ARG  BASE_IMAGE=alpine
ARG  BASE_VERSION=latest
FROM ${BASE_IMAGE}:${BASE_VERSION}

LABEL maintainer "Ming-Jui Chen <cutedogspark@gmail.com>"

ENV MIGRATE_VER=3.0.1 \
    UPX_VER=3.94

RUN apk update && \
    apk add --no-cache git openssh ca-certificates curl bash make build-base postgresql-client && \
    curl https://glide.sh/get | sh && \
    go get -u github.com/golang/dep/cmd/dep && \
    go get -u github.com/golang/protobuf/protoc-gen-go && \
    go get -u github.com/jteeuwen/go-bindata/... && \
    go get -u github.com/axw/gocov/gocov && \
    go get -u gopkg.in/matm/v1/gocov-html && \
    go get -u github.com/AlekSi/gocov-xml && \
    curl -L https://github.com/mattes/migrate/releases/download/v${MIGRATE_VER}/migrate.linux-amd64.tar.gz | tar xvz && mv migrate.linux-amd64 /usr/local/bin/migrate && chmod a+x /usr/local/bin/migrate && \
    curl -SL https://github.com/upx/upx/releases/download/v${UPX_VER}/upx-${UPX_VER}-i386_linux.tar.xz | tar xJv && mv upx-${UPX_VER}-i386_linux/upx /usr/local/bin/upx && rm -rf upx-${UPX_VER}-i386_linux && chmod a+x /usr/local/bin/upx && \
    rm -rf /var/cache/apk/* && rm -rf /var/lib/apt/lists/*

WORKDIR $GOPATH
