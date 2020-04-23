ARG BUILD_FROM=lmadean/mixaddon:latest
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

#set working dir
WORKDIR /config

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

