ARG HEKETI
FROM heketi/heketi:${HEKETI}
ARG KUBECTL
RUN curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBECTL}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl && \
    chmod +x /usr/local/bin/kubectl
