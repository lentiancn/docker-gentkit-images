#
# MIT License
#
# https://github.com/lentiancn/docker-gentkit-images/blob/main/LICENSE
#

#
# Stage 1 : Builder
#
ARG DEBIAN_IMAGE_TAG
FROM debian:${DEBIAN_IMAGE_TAG} AS builder

#
# Optimize system
#
RUN set -eux && \
    # Update package index \
    apt update -y && \
    # Install locale and configure \
    apt install --no-install-recommends locales -y && \
    sed -i '/^# *en_US.UTF-8/s/^# //' /etc/locale.gen && \
    locale-gen && \
    update-locale LANG="en_US.UTF-8" LC_ALL="en_US.UTF-8" && \
    echo 'export LANG=en_US.UTF-8' > /etc/profile.d/glocale.sh && \
    echo 'export LC_ALL=en_US.UTF-8' >> /etc/profile.d/glocale.sh && \
    # Clean \
    apt clean -y && apt autoremove -y && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /var/cache/apt/* && \
    # Reset welcome message \
    DEBIAN_VERSION=$(grep VERSION_ID /etc/os-release | cut -d'=' -f2) && \
    echo -e "\
Welcome to Debian Linux ${DEBIAN_VERSION} on Docker !" > /etc/motd

#
# Stage 2 : Production
#
FROM scratch AS production

#
# Copy resources
#
COPY --from=builder / /

#
# Set the working directory to /root for subsequent instructions
#
WORKDIR /root

#
# Set the default command to execute when running the image
#
CMD ["/bin/sh"]
