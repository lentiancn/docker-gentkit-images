#
# MIT License
#
# https://github.com/lentiancn/docker-gentkit-java/blob/main/LICENSE
#

#
# Stage 1 : Builder
#
FROM gentkit/alpine:latest AS builder

#
# Optimize system
#
RUN set -eu && \
    apk update --no-cache && \
    apk add --no-cache openjdk17 && \
    rm -rf /var/cache/apk/*

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
