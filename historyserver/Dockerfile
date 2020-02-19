FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8-1

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop historyserver

HEALTHCHECK CMD curl -f http://localhost:8188/ || exit 1

ENV YARN_CONF_yarn_timeline___service_leveldb___timeline___store_path=/hadoop/yarn/timeline
RUN mkdir -p /hadoop/yarn/timeline && \
    chown historyserver /hadoop/yarn/timeline && \
    chown historyserver /etc/hadoop && \
    chown historyserver /logs
VOLUME /hadoop/yarn/timeline

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER historyserver

EXPOSE 8188

CMD ["/run.sh"]
