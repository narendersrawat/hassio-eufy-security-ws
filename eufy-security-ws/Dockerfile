ARG BUILD_FROM
FROM $BUILD_FROM

WORKDIR /usr/src/app

COPY eufy-security-ws-3.1.0.tgz /tmp/eufy-security-ws-3.1.0.tgz

RUN \
    set -x \
    && apk add --no-cache \
        jq \
        nodejs \
        npm \
    && node --version \
    && case "$(node --version)" in v24.*) ;; *) echo "Expected Node 24, got $(node --version)" >&2; exit 1 ;; esac \
    && npm install --force /tmp/eufy-security-ws-3.1.0.tgz \
    && rm /tmp/eufy-security-ws-3.1.0.tgz

COPY run.sh /
RUN chmod a+x /run.sh

WORKDIR /data

CMD ["/run.sh"]