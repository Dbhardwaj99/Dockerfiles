# Install an image of Apache Kafka with ZooKeeper
FROM ubuntu:latest

# Install Java and other dependencies
RUN apt-get update && apt-get install -y openjdk-8-jdk curl

# Install Apache Kafka
RUN curl -O https://dlcdn.apache.org/kafka/3.5.0/kafka_2.13-3.5.0.tgz \
    && tar -xzf kafka_2.13-3.5.0.tgz \
    && mv kafka_2.13-3.5.0 /usr/local/kafka \
    && rm kafka_2.13-3.5.0.tgz

# Set environment variables
ENV KAFKA_HOME /usr/local/kafka
ENV PATH $PATH:$KAFKA_HOME/bin

# Expose ZooKeeper and Kafka ports
EXPOSE 2181 9092

# Start ZooKeeper and Kafka
CMD bash -c "zookeeper-server-start.sh $KAFKA_HOME/config/zookeeper.properties & kafka-server-start.sh $KAFKA_HOME/config/server.properties"
