This compose starts up a kafka broker, zookeeper, Schema registry and REST interface

You can use docker-app to generate new YMLs (docker app available here: https://github.com/docker/app)
To generate a new file:
```cli
docker-app init --single-file file
```

To render a new YML:
```cli
docker-app render
```

To render and run compose...
```cli
docker-app render | docker-compose -f - up
```

To change a specific value:
```cli
docker-app render --set kafka_listen_IP=172.16.2.123
```


You can interact with kafka using cli via the docker-compose exec.:

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
