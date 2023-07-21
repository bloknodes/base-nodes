FROM alpine as builder

WORKDIR /src

ENV CRYPTO_NAME=ethereum
ENV CRYPTO_VERSION=1.12.0
ENV CRYPTO_ARCH=amd64
ENV CRYPTO_COMMIT=e501b3b0

RUN apk --no-cache add openssl

RUN wget https://gethstore.blob.core.windows.net/builds/geth-linux-${CRYPTO_ARCH}-${CRYPTO_VERSION}-${CRYPTO_COMMIT}.tar.gz && \
    tar -xvf geth-linux-${CRYPTO_ARCH}-${CRYPTO_VERSION}-${CRYPTO_COMMIT}.tar.gz && \
    mv geth-linux-${CRYPTO_ARCH}-${CRYPTO_VERSION}-${CRYPTO_COMMIT}/geth /src/geth && \
    echo ${CRYPTO_VERSION} > /src/geth.version

FROM busybox

COPY --from=builder /src/geth /usr/bin/geth
COPY --from=builder /src/geth.version /opt/geth.version
RUN chmod +x /usr/local/geth/bin/geth
