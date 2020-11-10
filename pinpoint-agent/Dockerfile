FROM alpine:3.7

LABEL maintainer="Roy Kim <roy.kim@navercorp.com>"

RUN apk add --update curl bash

ARG PINPOINT_VERSION=${PINPOINT_VERSION:-1.8.5}
ARG INSTALL_URL=https://github.com/naver/pinpoint/releases/download/${PINPOINT_VERSION}/pinpoint-agent-${PINPOINT_VERSION}.tar.gz

COPY /pinpoint-agent-${PINPOINT_VERSION}.tar.gz pinpoint-agent.tar.gz
COPY /build/scripts/configure-agent.sh /usr/local/bin/

RUN chmod a+x /usr/local/bin/configure-agent.sh \
    && mkdir -p /pinpoint-agent \
    && chmod -R o+x /pinpoint-agent \
    && gunzip pinpoint-agent.tar.gz \
    && tar -xf pinpoint-agent.tar -C /pinpoint-agent \
    && rm pinpoint-agent.tar \
    && apk del curl \
    && rm /var/cache/apk/*

COPY /pinpoint-webrts-plugin-1.8.6-SNAPSHOT.jar pinpoint-webrts-plugin-1.8.6-SNAPSHOT.jar
RUN cp -f pinpoint-webrts-plugin-1.8.6-SNAPSHOT.jar /pinpoint-agent/plugin/ \
    && rm pinpoint-webrts-plugin-1.8.6-SNAPSHOT.jar

# COPY /jpetstoreplugin-1.8.4.jar jpetstoreplugin-1.8.4.jar
# RUN cp -f jpetstoreplugin-1.8.4.jar /pinpoint-agent/plugin/ \
#     && rm jpetstoreplugin-1.8.4.jar

VOLUME ["/pinpoint-agent"]

ENTRYPOINT ["/usr/local/bin/configure-agent.sh"]
CMD ["tail", "-f", "/dev/null"]