FROM ubuntu:16.04

# Install necessary packages for the installer
RUN apt-get update && apt-get install -y \
    lsb-release \
    build-essential \
    sed \
    sudo \
    tar \
    udev \
    wget \
    software-properties-common \
    && add-apt-repository ppa:ubuntu-toolchain-r/test \
    && apt-get update && apt-get install -y \
    gcc-4.9 \
    libstdc++6 \
    && apt-get clean

RUN cd /tmp && wget https://github.com/lhelontra/tensorflow-on-arm/releases/download/v1.9.0/tensorflow-1.9.0-cp35-none-linux_armv7l.whl \
    && pip3 install tensorflow-1.9.0-cp35-none-linux_armv7l.whl

# Copy over the NCSDK
COPY ./ ncsdk/

# Set the current working directory to the cloned ncsdk directory
WORKDIR "/ncsdk"

# Run the installer
RUN make install
