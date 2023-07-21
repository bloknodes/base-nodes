FROM busybox as builder

ENV CRYPTO_VERSION=0.21.2
ENV CRYPTO_ARCH=x86_64
ENV CRYPTO_NAME=bitcoin

WORKDIR /src
RUN wget https://bitcoincore.org/bin/bitcoin-core-${CRYPTO_VERSION}/bitcoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    tar -xf bitcoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    mv bitcoin-${CRYPTO_VERSION}/bin/bitcoind /src/bitcoind && \
    echo $CRYPTO_VERSION > /src/bitcoin.version

FROM debian:bookworm-slim
COPY --from=builder /src/bitcoind /usr/bin/bitcoind
COPY --from=builder /src/bitcoin.version /opt/bitcoin.version

