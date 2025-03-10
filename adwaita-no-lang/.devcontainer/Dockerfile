# Gets fedora 41 image
FROM quay.io/fedora/fedora:41

# Adds required developement dependencies
RUN dnf update -y && dnf install gtk4-devel ninja-build meson libadwaita-devel dbus-x11 libgee-devel json-glib-devel desktop-file-utils libglvnd-gles graphviz git vim sudo -y

# Creates the user
RUN useradd -m -s /bin/bash -G wheel adw && echo 'adw:dev' | sudo chpasswd
RUN usermod -aG render,video adw

# Allow adw to run sudo commands without a password
RUN echo 'adw ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/adw

# Switch to the user
USER adw
