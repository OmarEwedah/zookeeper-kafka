# kafka

FROM frekele/java

MAINTAINER Omar Ewedah <omar.ewedah@orange.com>

RUN apt-get update
RUN apt-get install tar
RUN wget -q http://www-eu.apache.org/dist/kafka/0.10.2.1/kafka_2.11-0.10.2.1.tgz -P / 
RUN tar xfz kafka_2.11-0.10.2.1.tgz
RUN rm kafka_2.11-0.10.2.1.tgz

WORKDIR kafka_2.11-0.10.2.1/

RUN sed -i "s|localhost:2181|10.254.58.61:2181 |g" config/server.properties
RUN sed -i "s|broker.id=0|# |g" config/server.properties
RUN echo "broker.id=$(ifconfig eth0 | grep -Eo 'inet (addr:)?([0-9]*\.){3}[0-9]*' | grep -Eo '([0-9]*\.){3}[0-9]*' |cut -d . -f 4)" >> config/server.properties
RUN sed -i "s|#advertised.listeners=PLAINTEXT://your.host.name:9092|advertised.listeners=PLAINTEXT://$(curl -s ifconfig.co):9092 |g" config/server.properties

EXPOSE 9092

CMD ["bin/kafka-server-start.sh", "config/server.properties"]
