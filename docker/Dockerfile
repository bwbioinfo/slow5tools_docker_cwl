# Use the official Alpine base image
FROM alpine:latest

# Install necessary packages in a single layer
RUN apk update && apk add --no-cache \
    bash \
    curl \
    hdf5-dev \
    zlib-dev \
    musl-dev \
    gcc \
    build-base && \
    rm -rf /var/cache/apk/*

# Define the version as a build argument for flexibility
ARG VERSION=v1.3.0
ENV VERSION=${VERSION}

# Download, extract, and build slow5tools, then clean up unnecessary files
RUN wget -q "https://github.com/hasindu2008/slow5tools/releases/download/${VERSION}/slow5tools-${VERSION}-release.tar.gz" && \
    tar xvf slow5tools-${VERSION}-release.tar.gz && \
    cd slow5tools-${VERSION} && \
    ./configure && \
    make install && \
    cd .. && \
    rm -rf slow5tools-${VERSION}* /var/cache/apk/*

# Set default command
CMD ["/usr/local/bin/slow5tools"]
