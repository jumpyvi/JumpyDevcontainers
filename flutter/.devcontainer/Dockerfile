# Use the official Debian image as a base
FROM debian:latest

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary packages
RUN apt-get update && apt-get install -y \
    sudo passwd curl cmake git unzip xz-utils zip libglu1-mesa \
    clang make git ninja-build pkg-config \
    libgtk-3-dev liblzma-dev libstdc++-12-dev tar wget dbus-x11 software-properties-common

# Set the password for the debian user
RUN useradd -m -s /bin/bash flutter && echo "flutter:root" | chpasswd

# Add debian user to sudoers
RUN usermod -aG sudo flutter

# Install Flutter
RUN curl https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_3.22.1-stable.tar.xz -o flutter.tar.xz && \
    tar -xf flutter.tar.xz && mv flutter /usr/bin && \
    rm flutter.tar.xz

# Add Flutter to the PATH
ENV PATH="/usr/bin/flutter/bin:${PATH}"

# Update and install Chromium
RUN apt-get update && apt-get install -y chromium

# Set the Chromium executable environment variable
ENV CHROME_EXECUTABLE="/usr/bin/chromium"

# Set the working directory
WORKDIR /home/flutter

# Switch to the new user
USER flutter

# Start DBus and keep the container running
CMD ["bash", "-c", "dbus-daemon --system --fork && tail -f /dev/null"]
