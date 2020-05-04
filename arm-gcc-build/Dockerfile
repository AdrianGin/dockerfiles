FROM alpine:3.7 AS stage
LABEL Description="Image for building embedded ARM on metal"
WORKDIR /work

ADD . /work

# Install any needed packages specified in requirements.txt
RUN apk add build-base \
            curl

RUN curl -L https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2 | tar -xjv

ENV PATH "/work/gcc-arm-none-eabi-9-2019-q4-major/bin:$PATH"

RUN curl -L https://github.com/Kitware/CMake/releases/download/v3.17.2/cmake-3.17.2-Linux-x86_64.sh > cmake-install.sh \
            && chmod +x cmake-install.sh && \
            mkdir cmake && \
            ./cmake-install.sh --skip-license --prefix=/work/cmake

ENV PATH "/work/cmake/bin:$PATH"
