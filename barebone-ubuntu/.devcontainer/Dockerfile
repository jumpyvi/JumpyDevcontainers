# Use the official Ubuntu image as a base
FROM ubuntu:latest

# Avoid prompts from apt
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary packages
RUN apt-get update && apt-get install -y sudo passwd

# Set the password for the ubuntu user
RUN echo "ubuntu:root" | chpasswd

# Add ubuntu user to sudoers
RUN usermod -aG sudo ubuntu

# Set the working directory
WORKDIR /home/ubuntu

# Switch to the new user
USER ubuntu

# Default command
CMD ["bash"]
