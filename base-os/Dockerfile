FROM quay.io/perl/base-os:v3.7

# Cache buster for occasionally resetting the cached images for the yum commands
ENV LAST_UPDATED 2018-09-29

ADD perl-modules /tmp/.modules

USER root

# install all the cpan stuff we need
RUN cpanm -M https://www.cpan.org -n < /tmp/.modules; rm -fr ~/.cpanm; rm -fr /usr/local/share/man;

RUN /usr/bin/geoipupdate-lite

ENV CBROOTLOCAL=/ntppool/
ENV CBROOT=/ntppool/combust

WORKDIR /ntppool

RUN addgroup ntppool && adduser -D -G ntppool ntppool

USER ntppool

EXPOSE 8299

USER ntppool
