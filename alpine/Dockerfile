FROM alpine:3.17

WORKDIR /

RUN apk add --no-cache \
        ca-certificates

RUN apk add --no-cache --virtual .build-deps \
        g++ \
        make \
        cmake \
        git \
        gperf \
        libressl-dev \
        zlib-dev \
        zlib-static \
        linux-headers;

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout a7a17b34b3c8fd3f7f6295f152746beb68f34d83 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    cmake --build . -j $(nproc) && \
    make install
