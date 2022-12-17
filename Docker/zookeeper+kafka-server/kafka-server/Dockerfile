FROM amazoncorretto:8u352-alpine3.16-jre
RUN apk update && apk add wget bash
RUN wget -O /tmp/kafka_2.12-3.3.1.tgz https://downloads.apache.org/kafka/3.3.1/kafka_2.12-3.3.1.tgz
RUN tar -xf /tmp/kafka_2.12-3.3.1.tgz -C /tmp/ && rm -f /tmp/kafka_2.12-3.3.1.tgz
COPY entrypoint.sh /usr/bin
RUN chmod +x /usr/bin/entrypoint.sh
RUN sed 's/^zookeeper.connect=.*/zookeeper.connect=zookeeper:2181/' /tmp/kafka_2.12-3.3.1/config/server.properties > .tmp 
RUN mv .tmp /tmp/kafka_2.12-3.3.1/config/server.properties 
EXPOSE 9092
CMD [ "/usr/bin/entrypoint.sh" ]
