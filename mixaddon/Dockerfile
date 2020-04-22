ARG BUILD_FROM=hassioaddons/base:7.0.4
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]


# Install mixlight environment
RUN \
    apk add --no-cache --virtual .build-dependencies \
        linux-headers \
        build-base \
        mosquitto-clients \
        python3-dev \
    \
    && apk add --no-cache \
        python3 \
    \
    && pip3 install --no-cache-dir --prefer-binary \        
        pyyaml \
        paho-mqtt \
        spidev \
        RPi.GPIO \
    \
    && find /usr/local \
        \( -type d -a -name test -o -name tests -o -name '__pycache__' \) \
        -o \( -type f -a -name '*.pyc' -o -name '*.pyo' \) \
        -exec rm -rf '{}' + \
    \
    && apk del --no-cache --purge .build-dependencies

# Install web environment
RUN apk add --no-cache nodejs-current yarn \
    && yarn global add npm \
    && yarn cache clean \
    && apk del yarn \
    && npm set unsafe-perm true     

# Copy the root filesystem
COPY rootfs /

#set working dir
WORKDIR /data

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

