# syntax=docker/dockerfile:1.20.0
FROM node:24.11.1-bookworm-slim

# Install dev tools
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
RUN apt update && apt install -yqq sudo git wget && apt clean && rm -rf /var/cache/apt
RUN echo 'node ALL=(ALL:ALL) NOPASSWD: ALL' >> /etc/sudoers

# Set up pnpm
ENV PNPM_HOME="/pnpm"
ENV PATH="$PNPM_HOME:$PATH"
RUN wget -qO- https://get.pnpm.io/install.sh | ENV="$HOME/.bashrc" SHELL="$(which bash)" bash -
RUN chown -R node:node "$PNPM_HOME"

# Set up workspace
WORKDIR /workspace
USER node
