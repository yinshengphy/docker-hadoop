FROM yinshengphy/hadoop3.2.1-java8

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop mapred

HEALTHCHECK CMD curl -f http://localhost:8188/ || exit 1

ENV YARN_CONF_yarn_timeline___service_leveldb___timeline___store_path=/hadoop/yarn/timeline
RUN mkdir -p /hadoop/yarn/timeline && \
    chown mapred /hadoop/yarn/timeline && \
    chown mapred /etc/hadoop && \
    chown mapred /logs
VOLUME /hadoop/yarn/timeline

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER mapred

EXPOSE 8188

CMD ["/run.sh"]
