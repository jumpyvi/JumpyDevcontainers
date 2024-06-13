FROM ubuntu:latest

# Install sudo to grant root privileges
RUN apt-get update \
    && apt-get install -y sudo \
    && rm -rf /var/lib/apt/lists/*

# Create the 'ubuntu' user with the same UID and GID as the host user
RUN echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/ubuntu

# Install Node.js as the 'ubuntu' user
USER ubuntu

RUN sudo apt-get update \
    && sudo apt-get install -y nodejs curl git dotnet-sdk-8.0 \
    && sudo rm -rf /var/lib/apt/lists/*

# Set the default user for the devcontainer to 'ubuntu'
USER ubuntu

# Install ef
RUN dotnet tool install --global dotnet-ef

# Set the default working directory
WORKDIR /home/ubuntu