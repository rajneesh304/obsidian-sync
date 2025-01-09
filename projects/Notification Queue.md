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
  --topic TutorialTopic
```

2. Kafka default port: `9092`
3. 