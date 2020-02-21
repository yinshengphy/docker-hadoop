FROM yinshengphy/hadoop3.2.1-java8

MAINTAINER yinshengphy@gmail.com

RUN groupadd -r hadoop && useradd -r -g hadoop yarn

HEALTHCHECK CMD curl -f http://localhost:8042/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

RUN chown yarn /etc/hadoop && \
    chown yarn /logs

USER yarn

EXPOSE 8042

CMD ["/run.sh"]
