#FROM harbor.ntppool.org/perlorg/base-os:3.18.4
FROM harbor.ntppool.org/perlorg/base-os@sha256:d1c870028623534d50425758b030fcbd2fc8d685a94f21ea661b01b9f181e1a0

RUN apk --no-cache upgrade
RUN apk --no-cache add vault \
  unzip cmake protobuf-dev

ADD perl-modules /tmp/.modules

USER root

# install all the cpan stuff we need
RUN cpanm -M https://www.cpan.org -n < /tmp/.modules \
  && rm -fr ~/.cpanm && rm -fr /usr/local/share/man;

ENV CBROOTLOCAL=/ntppool/
ENV CBROOT=/ntppool/combust

WORKDIR /ntppool

RUN addgroup ntppool && adduser -D -G ntppool ntppool

USER ntppool

EXPOSE 8299

USER ntppool
