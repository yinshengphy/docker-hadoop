FROM debian:9

MAINTAINER yinshengphy@gmail.com

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/

ENV HADOOP_VERSION 3.2.1
ENV HADOOP_URL https://www.apache.org/dist/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz

ENV HADOOP_HOME=/opt/hadoop-$HADOOP_VERSION
ENV HADOOP_CONF_DIR=/etc/hadoop
ENV MULTIHOMED_NETWORK=1
ENV USER=root
ENV PATH $HADOOP_HOME/bin/:$PATH

ADD entrypoint.sh /entrypoint.sh

#调整时区
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
          openjdk-8-jdk \
          net-tools \
          curl \
          openssh-client \
          netcat \
          gnupg && \
    rm -rf /var/lib/apt/lists/* && \
    curl -O https://dist.apache.org/repos/dist/release/hadoop/common/KEYS && \
    gpg --import KEYS && \
    set -x && \
    curl -fSL "$HADOOP_URL" -o /tmp/hadoop.tar.gz && \
    curl -fSL "$HADOOP_URL.asc" -o /tmp/hadoop.tar.gz.asc && \
    gpg --verify /tmp/hadoop.tar.gz.asc && \
    tar -xvf /tmp/hadoop.tar.gz -C /opt/ && \
    rm /tmp/hadoop.tar.gz* && \
    ln -s /opt/hadoop-$HADOOP_VERSION/etc/hadoop /etc/hadoop && \
    mkdir /opt/hadoop-$HADOOP_VERSION/logs && \
    ln -s /opt/hadoop-$HADOOP_VERSION/logs /logs && \
    mkdir /hadoop-data && \
    chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
