This compose starts up a kafka broker, zookeeper, Schema registry and REST interface

You can interact with kafka using cli via the docker-compose exec.:

__P.S.: Make sure you update the IP Address for KAFKA_ADVERTISED_LISTENERS__

# Examples:

## Creating a topic

```cli
docker-compose exec kafka kafka-topics --create --topic test --partitions 1 --replication-factor 1 --zookeeper zookeeper:2181
```

## Listing the topic

```cli
docker-compose exec kafka kafka-topics --describe --topic test --zookeeper zookeeper:2181
```

### Posting 42 generated messages to topic test:
```cli
docker-compose exec kafka  bash -c "seq 42 | kafka-console-producer --request-required-acks 1 --broker-list kafka:9092 --topic test && echo 'Produced 42 messages.'"
```
