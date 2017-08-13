# Zookeeper

FROM frekele/java

MAINTAINER Omar Ewedah <omar.ewedah@orange.com>

RUN apt-get update \
&& apt-get install tar \
&& wget -q http://www-eu.apache.org/dist/kafka/0.10.2.1/kafka_2.11-0.10.2.1.tgz -P /
&& tar xfz kafka_2.11-0.10.2.1.tgz \
&& rm kafka_2.11-0.10.2.1.tgz \

WORKDIR kafka_2.11-0.10.2.1/

CMD ["bin/zookeeper-server-start.sh", "config/zookeeper.properties"]
EXPOSE 2181 2888 3888
