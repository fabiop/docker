FROM t0mmyt/ubuntu:16.04
MAINTAINER Tom Taylor <tom@tommyt.co.uk>

EXPOSE 3000

ENV GRAFANA_USER grafana
ENV GRAFANA_HOME /usr/share/grafana
ENV CONF_DIR /etc/grafana
ENV WORK_DIR ${GRAFANA_HOME}
ENV DATA_DIR /var/lib/grafana
ENV LOG_DIR /var/log/grafana
ENV CONF_FILE ${CONF_DIR}/grafana.ini

ENV DEBIAN_FRONTEND=noninteractive
RUN wget -q https://grafanarel.s3.amazonaws.com/builds/grafana_3.0.1_amd64.deb && \
    apt-get install -yqq adduser libfontconfig && \
    dpkg -i grafana_3.0.1_amd64.deb

COPY grafana.ini ${CONF_FILE}

USER ${GRAFANA_USER}
WORKDIR ${GRAFANA_HOME}

ENTRYPOINT /usr/sbin/grafana-server --config=${CONF_FILE} cfg:default.paths.data=${DATA_DIR} cfg:default.paths.logs=${LOG_DIR}
