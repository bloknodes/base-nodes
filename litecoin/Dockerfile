FROM busybox as builder

WORKDIR /src

ENV CRYPTO_VERSION=0.21.2.1
ENV CRYPTO_ARCH=x86_64

RUN wget https://download.litecoin.org/litecoin-${CRYPTO_VERSION}/linux/litecoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    tar -xf litecoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    mv litecoin-${CRYPTO_VERSION}/bin/litecoind /src/litecoind && \
    echo ${CRYPTO_VERSION} > /src/litecoin.version

FROM debian:bookworm-slim
COPY --from=builder /src/litecoind /usr/bin/litecoind
COPY --from=builder /src/litecoin.version /opt/litecoin.version
