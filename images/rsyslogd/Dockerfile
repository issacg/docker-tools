FROM alpine:3.6
MAINTAINER Rich Braun "docker@instantlinux.net"
ARG BUILD_DATE
ARG VCS_REF
LABEL org.label-schema.build-date=$BUILD_DATE \
    org.label-schema.license=GPL-3.0 \
    org.label-schema.name=rsyslogd \
    org.label-schema.vcs-ref=$VCS_REF \
    org.label-schema.vcs-url=https://github.com/instantlinux/docker-tools

ENV TZ=US/Pacific
RUN apk add --update gzip logrotate rsyslog rsyslog-mysql tar xz && \
    rm -fr /var/log/* /var/cache/apk/*

VOLUME /var/log /etc/logrotate.d /etc/rsyslog.d
EXPOSE 514 514/udp
COPY logrotate.conf /etc/logrotate.conf

ADD entrypoint.sh /root/
ENTRYPOINT /root/entrypoint.sh
