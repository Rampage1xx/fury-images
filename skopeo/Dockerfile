FROM golang:1.14.3 as builder

ARG SKOPEO_VERSION=master

RUN apt-get update && \
        apt-get install -yqq libgpgme-dev libassuan-dev libbtrfs-dev libdevmapper-dev && \
        git clone https://github.com/containers/skopeo /go/src/github.com/containers/skopeo && \
        cd /go/src/github.com/containers/skopeo && \
        git checkout ${SKOPEO_VERSION} && \
        make binary-local

FROM ubuntu:20.04

COPY --from=builder /go/src/github.com/containers/skopeo/skopeo /usr/local/bin/skopeo
RUN apt-get update && \
        apt-get install -yqq curl libgpgme-dev libdevmapper-dev ca-certificates && \
        curl -Ls https://github.com/mikefarah/yq/releases/download/3.3.0/yq_linux_386 -o /usr/local/bin/yq && \
        chmod +x /usr/local/bin/yq && \
        curl -Ls https://github.com/stedolan/jq/releases/download/jq-1.6/jq-linux64 -o /usr/local/bin/jq && \
        chmod +x /usr/local/bin/jq
