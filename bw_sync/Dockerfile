# https://developers.home-assistant.io/docs/add-ons/configuration#add-on-dockerfile
ARG BUILD_FROM
FROM $BUILD_FROM

ARG BW_CLI_VERSION

# Execute during the build of the image
ARG TEMPIO_VERSION BUILD_ARCH

RUN apk add --no-cache jq npm && \
    npm install --no-progress --no-audit -g @bitwarden/cli@${BW_CLI_VERSION}

RUN \
    curl -sSLf -o /usr/bin/tempio \
    "https://github.com/home-assistant/tempio/releases/download/${TEMPIO_VERSION}/tempio_${BUILD_ARCH}"

# Copy root filesystem
COPY rootfs /