FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8-1

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop nodemanager

HEALTHCHECK CMD curl -f http://localhost:8042/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

RUN chown nodemanager /etc/hadoop && \
    chown nodemanager /logs

USER nodemanager

EXPOSE 8042

CMD ["/run.sh"]
