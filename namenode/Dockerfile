FROM yinshengphy/hadoop3.2.1-java8

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop hdfs

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1

ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
ENV CLUSTER_NAME=yinsheng_cluster
RUN mkdir -p /hadoop/dfs/name && \
    chown hdfs /hadoop/dfs/name && \
    chown hdfs /etc/hadoop && \
    chown hdfs /logs
VOLUME /hadoop/dfs/name

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER hdfs

EXPOSE 9870

CMD ["/run.sh"]
