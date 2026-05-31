#
# MIT License
#
# https://github.com/lentiancn/docker-gentkit-images/blob/main/LICENSE
#

#
# Stage 1 : Builder
#
FROM gentkit/alpine:latest AS builder

#
# Define argument
#
ARG JDK_MAJOR

#
# Optimize system
#
RUN set -eu && \
    apk update --no-cache && \
    if [ "${JDK_MAJOR}" = "8" ]; then \
        apk add --no-cache openjdk8 && \
    elif [ "${JDK_MAJOR}" = "11" ]; then \
        apk add --no-cache openjdk11 && \
    elif [ "${JDK_MAJOR}" = "17" ]; then \
        apk add --no-cache openjdk17 && \
    elif [ "${JDK_MAJOR}" = "21" ]; then \
        apk add --no-cache openjdk21 && \
    else \
        echo "Unsupported JDK version: ${JDK_MAJOR}" && exit 1; \
    fi && \
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
