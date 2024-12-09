# Prerequisites
1. [Kafka Setup](https://www.digitalocean.com/community/tutorials/how-to-install-apache-kafka-on-ubuntu-20-04) #kafka 
	```bash
curl "https://downloads.apache.org/kafka/3.9.0/kafka_2.13-3.9.0.tgz" -o ~/Downloads/kafka.tgz
	```
	1. Test command is wrong in above link. Command to use is here 
```bash
~/kafka/bin/kafka-topics.sh --create \
  --bootstrap-server localhost:9092 \
  --replication-factor 1 \
  --partitions 1 \
  --topic notification-topic
```

2. Kafka default port: `9092`
3. [Kafka Producer consumer sample app](https://medium.com/simform-engineering/kafka-integration-made-easy-with-spring-boot-b7aaf44d8889)
4. Producer command
```bash
./kafka-console-producer.sh --broker-list localhost:9092 --topic notification-topic < /home/kafka/jsondata.json
```