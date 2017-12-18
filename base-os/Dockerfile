FROM quay.io/perl/base-os:v3.2

# Cache buster for occasionally resetting the cached images for the yum commands
ENV LAST_UPDATED 2017-12-17

ADD perl-modules /tmp/.modules

USER root

# install all the cpan stuff we need
RUN cpanm -n < /tmp/.modules; rm -fr ~/.cpanm; rm -fr /usr/local/share/man;

# phantomjs for making .png graph images
RUN cd /usr/local; \
 curl -Lo /tmp/phantomjs.bz2 https://tmp.askask.com/2017/12/phantomjs-alpine-x86_64.tar.bz2 ; \
 tar -xvjf /tmp/phantomjs.bz2; \
 rm /tmp/phantomjs.bz2

RUN /usr/bin/geoipupdate-lite

ENV CBROOTLOCAL=/ntppool/
ENV CBROOT=/ntppool/combust

WORKDIR /ntppool

RUN addgroup ntppool && adduser -D -G ntppool ntppool

USER ntppool

EXPOSE 8299

USER ntppool
