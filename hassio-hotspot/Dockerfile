ARG BUILD_FROM
FROM $BUILD_FROM

LABEL João Loureiro <joaofl@gmail.com>

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ENV LANG C.UTF-8

# Install requirements for add-on
RUN sed -i '/v3\.\d*\/community/s/^#//' /etc/apk/repositories  && apk update && apk add --no-cache    \
    avahi                               \
    bash jq iw net-tools                \
    sudo busybox-extras                 \
    eudev networkmanager networkmanager-cli networkmanager-tui \
    hostapd iptables                    \
    linux-firmware-other                \
    linux-firmware-ath6k                \
    linux-firmware-ath10k               \
    linux-firmware-ath9k_htc &&         \
    rm -rf /var/cache/apk/*

COPY hostapd.conf /
COPY udhcpd.conf /etc/udhcpd.conf
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]
