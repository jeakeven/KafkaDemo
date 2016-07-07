# KafkaDemo

1、修改config/zookeeper.properties文件：clientPort=9876

2、修改config/server.properties文件：zookeeper.connect=localhost:9876

3、启动zookeeper： bin/zookeeper-server-start.sh config/zookeeper.properties

4、启动kafka：bin/kafka-server-start.sh config/server.properties

5、创建topic：bin/kafka-topics.sh --create --zookeeper localhost:9876 --replication-factor 1 --partitions 1 --topic test

6、查看topic：bin/kafka-topics.sh --list --zookeeper localhost:9876

7、producer生产消息：bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
This is a message

8、consumer消费消息：bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning
This is a message


注意：

启动kakfa（见4）出错的时候：一般是内存不够，可以修改kafka broker的heap设置

在bin/kafka-server-start.sh文件中，将如下内容：export KAFKA_HEAP_OPTS="-Xmx1G -Xms1G"

修改成：export KAFKA_HEAP_OPTS="-Xmx200m -Xms200m"

