# Installation steps

Step 1. Download kafka kafka_2.12-2.8.2.tgz using the below command using terminal
curl "https://downloads.apache.org/kafka/2.8.2/kafka_2.12-2.8.2.tgz" -o ~/Downloads/kafka.tgz

Step 2. make kafka directory.
mkdir /kafka

Step 3.changed the directory to kafka
cd /kafka

Step 4. Move kafka.tgz file from Download directory to kafka directory
sudo mv /home/cloudera/Downloads/kafka.tgz /home/cloudera/kafka

Step 5. Extract the compressed file
tar -xvzf kafka.tgz --strip 1

Step 6. Check zookeeper port(2181) is available or not
ps -aux | grep 2181

Step 7. Start ZooKeeper Server
bin/zookeeper-server-start.sh config/zookeeper.properties

Step 8. Make sure ZooKeeper running on port 2181.
Go to /home/cloudera/kafka/config and look zookeeper.properties
cat /home/cloudera/kafka/config/zookeeper.properties

Step 9. Stop ZooKeeper Server
bin/zookeeper-server-stop.sh config/zookeeper.properties

Step 10. Check Broker port(9092) is available or not
ps -aux | grep 9092

Step 11. Start Broker server
bin/kafka-server-start.sh config/server.properties

Step 12. Make sure Broker running on port 9092.
Go to /home/cloudera/kafka/config and look server.properties
cat /home/cloudera/kafka/config and look server.properties

cat /home/cloudera/kafka/config/server.properties

Step 13. Stop Broker server
bin/kafka-server-stop.sh config/server.properties

Step 14. Keep this terminal open and open a new terminal. Now Start a Topic
bin/kafka-topics.sh --create --topic my-kafka-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

Step 15. Now you can send message to this standby topic , so create a data Producer
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic my-kafka-topic

Step 16. Write the message here, (ex: Hello Kafka!)
Hello kafka!

Step 17. Open a new Terminal. Create a Consumer to get the value from Producer.
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my-kafka-topic --from-beginning

Step 18. Now you can see the message from consumer whatever you give input on producer.
 