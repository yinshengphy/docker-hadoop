FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8-1

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop namenode

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1

ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
ENV CLUSTER_NAME=yinsheng_cluster
RUN mkdir -p /hadoop/dfs/name && \
    chown namenode /hadoop/dfs/name && \
    chown namenode /etc/hadoop && \
    chown namenode /logs
VOLUME /hadoop/dfs/name

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER namenode

EXPOSE 9870

CMD ["/run.sh"]
