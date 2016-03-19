FROM ajiniesta/alpinejava:jre8u74

USER root

RUN apk update && apk upgrade

RUN apk add curl tar ca-certificates

RUN mkdir -p /opt/zookeeper && \
    curl -Ls 'http://apache.rediris.es/zookeeper/zookeeper-3.3.6/zookeeper-3.3.6.tar.gz' -H 'Cookie: oraclelicense=accept-securebackup-cookie' | \
    tar --strip-components=1 -xz -C /opt/zookeeper

RUN cp /opt/zookeeper/conf/zoo_sample.cfg /opt/zookeeper/conf/zoo.cfg

RUN apk del tar curl libcurl libssh2 ca-certificates openssl

RUN rm -rf /var/cache/apk/*

RUN mkdir -p /tmp/zookeeper

EXPOSE 2181

CMD /opt/zookeeper/bin/zkServer.sh start-foreground
