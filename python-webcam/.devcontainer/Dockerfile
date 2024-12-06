FROM mcr.microsoft.com/devcontainers/python:1-3.12-bullseye

RUN apt-get update -y && apt-get install libgl1 x11-apps -y

USER vscode

RUN curl -fsSL https://pixi.sh/install.sh | bash