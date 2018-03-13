FROM fedora:27

RUN dnf upgrade -y && \
    dnf install -y java-1.8.0-openjdk

ENV DOCKERIZE_VERSION v0.6.0
RUN curl -LO https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

ENV KAFKA_VERSION 0.10.2.0

ADD kafka_2.11-$KAFKA_VERSION.tgz /usr/local/opt/
ADD server.properties.tmpl /etc/kafka/

EXPOSE 9092

CMD dockerize -template /etc/kafka/server.properties.tmpl:/etc/kafka/server.properties /usr/local/opt/kafka_2.11-$KAFKA_VERSION/bin/kafka-server-start.sh /etc/kafka/server.properties
