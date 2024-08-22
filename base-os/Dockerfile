FROM harbor.ntppool.org/perlorg/base-os:3.20.2

RUN apk --no-cache upgrade
RUN apk --no-cache add \
  unzip cmake protobuf-dev

ADD perl-modules /tmp/.modules

USER root

# RUN cpanm https://tmp.askask.com/2023/11/Plack-Middleware-OpenTelemetry-0.233320-TRIAL.tar.gz

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
