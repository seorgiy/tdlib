FROM buildpack-deps:buster-scm

WORKDIR /

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git cmake build-essential gperf libssl-dev zlib1g-dev

RUN git clone https://github.com/tdlib/td.git && \
    cd td && \
    git checkout a7a17b34b3c8fd3f7f6295f152746beb68f34d83 && \
    mkdir build && \
    cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    cmake --build . && \
    make install