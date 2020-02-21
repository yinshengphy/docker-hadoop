FROM yinshengphy/hadoop3.2.1-java8

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop hdfs

HEALTHCHECK CMD curl -f http://localhost:9864/ || exit 1

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop/dfs/data
RUN mkdir -p /hadoop/dfs/data && \
    chown hdfs /hadoop/dfs/data && \
    chown hdfs /etc/hadoop && \
    chown hdfs /logs

VOLUME /hadoop/dfs/data

ADD run.sh /run.sh
RUN chmod a+x /run.sh

USER hdfs

EXPOSE 9864

CMD ["/run.sh"]
