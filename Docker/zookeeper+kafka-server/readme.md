### Kakfa + Zookeeper

```docker
docker create network kafka
cd zookeeper/ && docker build -t zookeeper:v1 .
docker run -d -p 2181:2181 --net kafka --name zookeeper zookeeper:v1
cd kafka-server/ && docker build -t kafka-server:v1 .
docker run -d -p 9092:9092 --net kafka --name kafka-server kafka-server:v1
```
