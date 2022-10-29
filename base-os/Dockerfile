FROM harbor.ntppool.org/perlorg/base-os:3.16.2


RUN apk --no-cache upgrade
RUN apk --no-cache add vault

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
