FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8-1

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop resourcemanager

HEALTHCHECK CMD curl -f http://localhost:8088/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

RUN chown resourcemanager /etc/hadoop&& \
    chown resourcemanager /logs

USER resourcemanager

EXPOSE 8088

CMD ["/run.sh"]
