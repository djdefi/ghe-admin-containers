FROM debian:jessie

RUN apt-get update; apt-get --yes upgrade
RUN apt-get --yes install \
    collectd collectd-utils

COPY collectd.conf /etc/collectd/

EXPOSE 25826
CMD /usr/sbin/collectd -C /etc/collectd/collectd.conf -f
