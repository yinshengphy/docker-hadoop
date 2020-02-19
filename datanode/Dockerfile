FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8-1

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop datanode

HEALTHCHECK CMD curl -f http://localhost:9864/ || exit 1

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop/dfs/data
RUN mkdir -p /hadoop/dfs/data && \
    chown datanode /hadoop/dfs/data && \
    chown datanode /etc/hadoop && \
    chown datanode /logs

VOLUME /hadoop/dfs/data

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER datanode

EXPOSE 9864

CMD ["/run.sh"]
