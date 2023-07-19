FROM busybox as builder

ENV CRYPTO_VERSION=0.21.2

WORKDIR /src
RUN wget https://bitcoincore.org/bin/bitcoin-core-${CRYPTO_VERSION}/bitcoin-${CRYPTO_VERSION}-x86_64-linux-gnu.tar.gz && \
    tar -xf bitcoin-${CRYPTO_VERSION}-x86_64-linux-gnu.tar.gz && \
    mv bitcoin-${CRYPTO_VERSION}/bin/bitcoind /src/bitcoind && \
    echo $CRYPTO_VERSION > /src/bitcoin.version

FROM busybox
COPY --from=builder /src/bitcoind /usr/local/bitcoin/bin/bitcoind
COPY --from=builder /src/bitcoin.version /usr/local/bitcoin/docs/bitcoin.version

