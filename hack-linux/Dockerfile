# ################################################################################
#  Copyright (c) 2026  Claudio André <portfolio-2026br at claudioandre.slmail.me>
#              ___                _      ___       _
#             (  _`\             ( )_  /'___)     (_ )  _
#             | |_) )  _    _ __ | ,_)| (__   _    | | (_)   _
#             | ,__/'/'_`\ ( '__)| |  | ,__)/'_`\  | | | | /'_`\
#             | |   ( (_) )| |   | |_ | |  ( (_) ) | | | |( (_) )
#             (_)   `\___/'(_)   `\__)(_)  `\___/'(___)(_)`\___/'
#
# This program comes with ABSOLUTELY NO WARRANTY; express or implied.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, as expressed in version 2, seen at
# https://www.gnu.org/licenses/gpl-2.0.html
# ################################################################################
# Dockerfile usado para explorar a CVE-2025-32463
# More info at https://github.com/portfolio-2026br/security

FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Prepare the environment
RUN apt-get update -y \
    && apt-get install -y --no-install-recommends \
        gcc=* libc6-dev=* ca-certificates=* libnss3-tools=* \
        sudo=1.9.15p5-3ubuntu5 \
# Clean up
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

# ==================================================================
# Setup
# ------------------------------------------------------------------
ARG GID=1001
ARG UID=1001
ARG USERNAME="normalzinho"
RUN groupadd -g "${GID}" -o "${USERNAME}" \
    && useradd -m -u "${UID}" -g "${GID}" -o -s /bin/bash -p "$(openssl passwd -1 123456)" -l "${USERNAME}"
USER $USERNAME

# Copiar a ferramenta que explora falha para a minha imagem
COPY local/abra-cadabra.sh /home/normalzinho/abra-cadabra.sh

HEALTHCHECK NONE
