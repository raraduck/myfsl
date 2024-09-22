# Use Ubuntu 18.04 as base image
FROM ubuntu:18.04

# Set non-interactive mode for APT
ENV DEBIAN_FRONTEND=noninteractive

# Update and install necessary dependencies, add NeuroDebian repository, and clean up in a single RUN command
RUN apt update && apt install -y --no-install-recommends wget curl gnupg ca-certificates \
    && wget -O /etc/apt/sources.list.d/neurodebian.sources.list http://neuro.debian.net/lists/bionic.cn-bj1.full \
    && mkdir -p /root/.gnupg && chmod 700 /root/.gnupg \
    && gpg --no-default-keyring --keyring gnupg-ring:/etc/apt/trusted.gpg.d/neurodebian.gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys 0xA5D32F012649A5A9 \
    && chmod 644 /etc/apt/trusted.gpg.d/neurodebian.gpg \
    && apt-get update \
    && apt-get install -y --no-install-recommends fsl-complete \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /root/.gnupg

# Set entrypoint to ensure fsl.sh is executed
# v0.2
#RUN echo "source /etc/fsl/5.0/fsl.sh" >> ~/.bashrc
#CMD ["/bin/bash"]
# v0.1
RUN echo "source /etc/fsl/5.0/fsl.sh" >> ~/.bashrc
ENTRYPOINT ["/bin/bash", "-c", "source /etc/fsl/5.0/fsl.sh && exec \"$@\"", "--"]
CMD ["flirt", "-version"]
