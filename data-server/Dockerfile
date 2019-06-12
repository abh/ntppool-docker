FROM almir/webhook:2.6.9 AS webhook

FROM quay.io/ntppool/base-os:v3.9.1
USER root
RUN apk --no-cache upgrade
WORKDIR /opt
COPY --from=webhook /usr/local/bin/webhook /usr/local/bin/webhook
RUN git clone https://github.com/abh/pgeodns.git
RUN adduser -D -u 1050 data-server
WORKDIR /home/data-server
#USER data-server
