# Use the official Racket image (Debian-based)
FROM racket/racket:8.17-full

# Optional: Install GUI dependencies if you want gracket to work
RUN apt-get update && apt-get install -y \
    sudo git fontconfig libffi-dev libcairo2 libjpeg62-turbo \
    libglib2.0-0 libpango-1.0-0 libgtk2.0-0 libx11-6 libxrender1 \
    libxt6 libsm6 libice6 \
    && apt-get clean

# Create a user (non-root)
ENV USER=racket
RUN useradd -m -s /bin/bash $USER && \
    echo "$USER ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Set working directory and switch to the new user
WORKDIR /home/$USER
USER $USER

CMD [ "racket", "--version" ]