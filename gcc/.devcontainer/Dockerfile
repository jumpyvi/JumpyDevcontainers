FROM alpine:3.22.1

# Install build tools, sudo, and bash
RUN apk update && apk add --no-cache \
    build-base \
    sudo \
    bash


# Create user 'comp' with home directory and bash as default shell
RUN adduser -D -s /bin/bash comp && \
    echo "comp ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Switch to user 'comp'
USER comp