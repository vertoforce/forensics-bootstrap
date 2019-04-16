# From https://github.com/jgarber623/docker-forensics-tools/
# with slight modifications

FROM debian:9

# Install dependencies
RUN apt-get update && \
      DEBIAN_FRONTEND=noninteractive \
      apt-get install -y \
      default-jre \
      forensics-all \
      forensics-extra

# Post-installation cleanup
RUN apt-get autoclean -y && \
    rm -rf /tmp/* /var/tmp/*

# Set default working directory
WORKDIR /workspace
