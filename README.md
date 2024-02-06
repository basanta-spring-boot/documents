# documents

## Open Source Kafka Startup in local ##

1. Start Zookeeper Server

    ```sh bin/zookeeper-server-start.sh config/zookeeper.properties```

   ```bin\windows\zookeeper-server-start.bat config\zookeeper.properties```

3. Start Kafka Server / Broker

    ```sh bin/kafka-server-start.sh config/server.properties```

   ```bin\windows\kafka-server-start.bat config\server.properties```

5. Create topic

    ```sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic NewTopic --partitions 3 --replication-factor 1```

   ```bin\windows\kafka-topics.bat --create --topic user-topic --bootstrap-server localhost:9092```

   ```bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --create --topic user-topic --partitions 3 --replication-factor 1```

7. list out all topic names

    ``` sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --list ```
   
    ```bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --list ```

9. Describe topics
  
    ``` sh bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic NewTopic ```

    ``` bin\windows\kafka-topics.bat --bootstrap-server localhost:9092 --describe --topic user-topic```

11. Produce message

    ```sh bin/kafka-console-producer.sh --broker-list localhost:9092 --topic NewTopic```

    ```bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic user-topic```

    ```bin\windows\kafka-console-producer.bat --topic user-topic --bootstrap-server localhost:9092```


13. consume message

    ``` sh bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic NewTopic --from-beginning ```

    ```bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic user-topic --from-beginning```

    ```bin\windows\kafka-console-consumer.bat --topic user-topic --from-beginning --bootstrap-server localhost:9092```


## Confluent Kafka Community Edition in local ##

1. Start Zookeeper Server

    ```bin/zookeeper-server-start etc/kafka/zookeeper.properties```

2. Start Kafka Server / Broker

    ```bin/kafka-server-start etc/kafka/server.properties```

3. Create topic

    ```bin/kafka-topics --bootstrap-server localhost:9092 --create --topic NewTopic1 --partitions 3 --replication-factor 1```

4. list out all topic names

    ``` bin/kafka-topics --bootstrap-server localhost:9092 --list ```

5. Describe topics
  
    ``` bin/kafka-topics --bootstrap-server localhost:9092 --describe --topic NewTopic1 ```

6. Produce message

    ```bin/kafka-console-producer --broker-list localhost:9092 --topic NewTopic1```


7. consume message

    ```bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic NewTopic1 --from-beginning ```
    
8. Send CSV File data to kafka    

   ```bin/kafka-console-producer --broker-list localhost:9092 --topic NewTopic1 <bin/customers.csv```
   
   
