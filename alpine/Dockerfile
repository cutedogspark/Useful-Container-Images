ARG  BASE_IMAGE=alpine
ARG  BASE_VERSION=latest
FROM ${BASE_IMAGE}:${BASE_VERSION}

LABEL maintainer "Ming-Jui Chen <cutedogspark@gmail.com>"

RUN apk update && \
    apk add --no-cache \
    bash curl iputils tar bzip2 openssl ca-certificates && \
    rm -rf /var/cache/apk/* && rm -rf /var/lib/apt/lists/*

WORKDIR /
