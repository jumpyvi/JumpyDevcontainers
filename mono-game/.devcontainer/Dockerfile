# Use latest LTS from Ubuntu
FROM ubuntu:noble

# Adds required developement dependencies
RUN apt-get update -y && apt-get install fonts-cantarell fzf just dbus-x11 dotnet-sdk-8.0 aspnetcore-runtime-8.0 wget curl p7zip-full desktop-file-utils git sudo -y

# RUN dpkg --add-architecture i386 && apt-get update && apt-get install wine32:i386 wine64 -y

# Installs the semi-required fonts
RUN echo "ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true" | debconf-set-selections ; apt-get install -y ttf-mscorefonts-installer

# Deletes the default 'ubuntu' user if it exists (to avoid conflicts with UID 1000)
RUN userdel -r ubuntu || true

# Creates the user with a fixed UID of 1000
RUN useradd -m -s /bin/bash -G sudo -u 1000 mono && echo 'mono:dev' | sudo chpasswd

# Allow mono to run sudo commands without a password
RUN echo 'mono ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/mono

# Switch to the user
USER mono

# Install wine script from mono
# RUN wget -qO- https://monogame.net/downloads/net8_mgfxc_wine_setup.sh | bash

# Adds just completion to ~/.bashrc
RUN grep -qxF 'source <(just --completions bash)' /home/mono/.bashrc || echo 'source <(just --completions bash)' >> /home/mono/.bashrc
