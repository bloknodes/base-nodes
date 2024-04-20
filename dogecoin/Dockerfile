FROM busybox as builder

WORKDIR /src

ARG CRYPTO_ARCH=x86_64
ENV CRYPTO_VERSION=1.14.7
ENV CRYPTO_ARCH=$CRYPTO_ARCH

RUN wget https://github.com/dogecoin/dogecoin/releases/download/v${CRYPTO_VERSION}/dogecoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    tar -xf dogecoin-${CRYPTO_VERSION}-${CRYPTO_ARCH}-linux-gnu.tar.gz && \
    mv dogecoin-${CRYPTO_VERSION}/bin/dogecoind /src/dogecoind && \
    echo ${CRYPTO_VERSION} > /src/dogecoin.version

FROM busybox

COPY --from=builder /src/dogecoind /usr/bin/dogecoind
COPY --from=builder /src/dogecoin.version /opt/dogecoin.version
