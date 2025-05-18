# Dockerfile for Debian Bookworm with curl installed
FROM debian:bookworm

# Update and upgrade the system
RUN apt-get update --fix-missing && apt-get -y upgrade --fix-missing

# Install packages
RUN apt-get install -y --fix-missing \
    apt-utils \
    sudo

# Create a sudo user
RUN useradd -u 1000 -m user --create-home --shell /bin/bash
RUN echo "emlinux ALL=(ALL) NOPASSWD: ALL" | tee -a /etc/sudoers

CMD ["bash"]
