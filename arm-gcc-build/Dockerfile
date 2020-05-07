FROM debian:bullseye-slim
LABEL Description="Image for building embedded ARM on metal"
WORKDIR /work

# Install any needed packages specified in requirements.txt
RUN apt-get update && apt-get upgrade -y && \ 
    apt-get install -y build-essential \
            curl

ARG ARMGCC_DIR="/opt"
ARG CMAKE_DIR="/usr/local"


RUN curl -L https://developer.arm.com/-/media/Files/downloads/gnu-rm/9-2019q4/gcc-arm-none-eabi-9-2019-q4-major-x86_64-linux.tar.bz2 | tar -xjv -C ${ARMGCC_DIR}

RUN curl -L https://github.com/Kitware/CMake/releases/download/v3.17.2/cmake-3.17.2-Linux-x86_64.sh > cmake-install.sh \
            && chmod +x cmake-install.sh && \
            ./cmake-install.sh --skip-license --prefix=${CMAKE_DIR}

ENV PATH "${ARMGCC_DIR}/gcc-arm-none-eabi-9-2019-q4-major/bin:$PATH"

ENV ARMGCC_DIR="${ARMGCC_DIR}/gcc-arm-none-eabi-9-2019-q4-major"



