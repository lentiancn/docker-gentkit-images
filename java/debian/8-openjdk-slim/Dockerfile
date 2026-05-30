#
# MIT License
#
# https://github.com/lentiancn/docker-gentkit-images/blob/main/LICENSE
#

#
# Stage 1 : Builder
#
FROM gentkit/debian:latest AS builder

#
# Optimize system
#
RUN set -eu && \
    apt update && \
    apt install -y openjdk-8-jdk && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

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
CMD ["/bin/sh", "-c", "java -version; exec /bin/sh"]
