FROM library/python:3.10-bookworm

ARG USER=vscode
ARG DEBIAN_FRONTEND=noninteractive

COPY requirements.txt /tmp/

RUN apt update \
    && apt install -y --no-install-recommends sudo \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && useradd -m -s /usr/bin/bash ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER} \
    && python -m pip install -r /tmp/requirements.txt \
    && rm /tmp/requirements.txt