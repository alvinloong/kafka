# [GETTING STARTED](https://kafka.apache.org/documentation/#gettingStarted)

## [Quick Start](https://kafka.apache.org/quickstart)

### [STEP 1: GET KAFKA](https://kafka.apache.org/quickstart#quickstart_download)

```
sudo apt-get install openjdk-8-jdk
mkdir -p ~/soft/zookeeper/
tar -zxvf apache-zookeeper-3.6.1-bin.tar.gz -C ~/soft/zookeeper/
mkdir -p ~/soft/kafka/
tar -zxvf kafka_2.13-2.6.0.tgz -C ~/soft/kafka/
```

```
export ZOOKEEPER_HOME=$(pwd)
export KAFKA_HOME=$(pwd)
```

```
vi ~/.bashrc
```

```
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export ZOOKEEPER_HOME=/home/alvin/soft/zookeeper/apache-zookeeper-3.6.1-bin
export PATH=$ZOOKEEPER_HOME/bin:$PATH
export KAFKA_HOME=/home/alvin/soft/kafka/kafka_2.13-2.6.0
export PATH=$KAFKA_HOME/bin:$PATH
```

```
source ~/.bashrc
```

### [STEP 2: START THE KAFKA ENVIRONMENT](https://kafka.apache.org/quickstart#quickstart_startserver)

```
cd $ZOOKEEPER_HOME
mkdir data
cp conf/zoo_sample.cfg conf/zoo.cfg
vi conf/zoo.cfg
```

```
dataDir=/home/alvin/soft/zookeeper/apache-zookeeper-3.6.1-bin/data
```

```
bin/zkServer.sh start
jps
```

```
cd $KAFKA_HOME
mkdir data
mkdir logs
```

```
vi config/server.properties
```

```
broker.id=0
log.dirs=$KAFKA_HOME/logs
zookeeper.connect=localhost:2181
```

```
bin/kafka-server-start.sh config/server.properties
```

### [STEP 3: CREATE A TOPIC TO STORE YOUR EVENTS](https://kafka.apache.org/quickstart#quickstart_createtopic)

```
bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092
bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092
```

### [STEP 4: WRITE SOME EVENTS INTO THE TOPIC](https://kafka.apache.org/quickstart#quickstart_send)

```
bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
```

### [STEP 5: READ THE EVENTS](https://kafka.apache.org/quickstart#quickstart_consume)

```
bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
```

