# Create topic
```docker exec kafka-1 kafka-topics --bootstrap-server kafka-1:19092 --replication-factor 3 --partitions 1 --create --topic quickstart```

# Ensure that topic is created in the broker
```docker exec kafka-1 kafka-topics \
     --bootstrap-server kafka-1:19092 -list
```

# Write messages to the topic
```docker exec --interactive --tty zookeeper-1 kafka-console-producer --bootstrap-server kafka-1:19092,kafka-2:29092,kafka-3:39092 --topic quickstart```

# Read messages from the topic
```docker exec --interactive --tty kafka-1 kafka-console-consumer --bootstrap-server kafka-1:19092 --topic quickstart --from-beginning```

# Figure out which broker is leader
```docker exec zookeeper-1 kafka-topics --bootstrap-server kafka-1:19092 --topic quickstart --describe```