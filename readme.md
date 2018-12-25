# Purpose 
Show how Kafka deals with large binary files. 

Although, we know already that Kafka is not designed for this scenario, in this case we tried to show how this is not working, if you need to prove it to someone

# Steps to reproduce
1. Have Kafka installed in a local environment
2. start kafka
4. execute with a text file
5. execute with a binary file

# Execution in detail
Step 1:
* Download latest version from kafka.apache.com and extract into working dir
* Add Kafka/bin to path

Step 2: 
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
bin/kafka-topics.sh --create --topic binary_text --zookeeper localhost:2181 --replication-factor 1 --partitions 1
bin/kafka-topics.sh --create --topic text_test --zookeeper localhost:2181 --replication-factor 1 --partitions 1

Step 3:
connect-standalone.sh config/connect-standalone.properties config/
connect-txt-file-source.properties config/connect-txt-file-sink.properties
 
connect-standalone.sh config/connect-standalone.properties config/
connect-bin-file-source.properties config/connect-bin-file-sink.properties