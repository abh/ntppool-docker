FROM quay.io/perl/base-os:v3.0

# Cache buster for occasionally resetting the cached images for the yum commands
ENV LAST_UPDATED 2017-09-20

ADD perl-modules /tmp/.modules

USER root

# install all the cpan stuff we need
RUN cpanm -n < /tmp/.modules; rm -fr ~/.cpanm; rm -fr /usr/local/share/man;

# phantomjs for making .png graph images
RUN cd /usr/local; curl -Lo /tmp/phantomjs.bz2 https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2; tar -xvjf /tmp/phantomjs.bz2; mv phantomjs-2.1.1-linux-x86_64 phantomjs; rm /tmp/phantomjs.bz2

RUN /usr/bin/geoipupdate-lite

ENV CBROOTLOCAL=/ntppool/
ENV CBROOT=/ntppool/combust

WORKDIR /ntppool

RUN addgroup ntppool && adduser -D -G ntppool ntppool

USER ntppool

EXPOSE 8299

USER ntppool

#CMD ./docker-run
