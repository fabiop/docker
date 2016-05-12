FROM t0mmyt/ubuntu:16.04
MAINTAINER Tom Taylor <tom@tommyt.co.uk>

EXPOSE 2003 8083 8086 8090 8099

ENV DEBIAN_FRONTEND=noninteractive
RUN wget -q https://dl.influxdata.com/influxdb/releases/influxdb_0.12.2-1_amd64.deb && \
    dpkg -i influxdb_0.12.2-1_amd64.deb

COPY influxdb.conf /etc/influxdb/influxdb.conf

USER influxdb:influxdb

ENTRYPOINT ["/usr/bin/influxd", "-config", "/etc/influxdb/influxdb.conf"]
