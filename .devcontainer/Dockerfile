# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.245.2/containers/debian/.devcontainer/base.Dockerfile

# [Choice] Debian version (use bullseye on local arm64/Apple Silicon): bullseye, buster
ARG VARIANT="buster"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# These dependencies are required by Nix.
RUN apt update -y
RUN apt -y install --no-install-recommends curl xz-utils

USER vscode

# Install nix
ARG NIX_INSTALL_SCRIPT=https://nixos.org/nix/install
RUN curl -fsSL ${NIX_INSTALL_SCRIPT} | sh -s -- --no-daemon
ENV PATH /home/vscode/.nix-profile/bin:${PATH}

# install devbox
RUN sudo mkdir /devbox && sudo chown vscode /devbox
RUN curl -fsSL https://get.jetpack.io/devbox | FORCE=1 bash
COPY --chown=vscode devbox.json /devbox/devbox.json
RUN devbox shell --config /devbox/devbox.json -- echo "Nix Store Populated"
ENV PATH /devbox/.devbox/nix/profile/default/bin:${PATH}
