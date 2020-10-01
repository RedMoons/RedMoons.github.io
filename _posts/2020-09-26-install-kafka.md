---
title: "Kafka 튜토리얼 01 - Kafka 설치"
excerpt: "Kafka 설치"

categories:
  - kafka
tags:
  - kafka
  - 카프카
  - install
  - 설치
  - tutorial
  - 튜토리얼
last_modified_at: 2020-10-01T08:06:00-05:00
---

## 설치파일 다운로드
카프카를 Mac에서 설치해 보겠습니다. [다운로드 카프카](https://archive.apache.org/dist/kafka/2.2.0/kafka_2.12-2.2.0.tgz) 위 링크를 클릭해서 카프카 2.2 tgz 파일을 다운받습니다. 다운로드가 안될 때에는 여기서 다운받습니다. [공식 홈페이지](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.2.0/kafka_2.12-2.2.0.tgz) 그러고 나서 해당 파일을 압축해제해 줍니다.
```bash
tar -xzf kafka_2.12-2.2.0.tgz
cd kafka_2.12-2.2.0
```

## 서버 시작하기
카프카는 주키퍼를 이용하기 때문에, 우선 주키퍼 서버를 시작해야 합니다. 아래 커맨드를 이용해 싱글 노드의 주키퍼 인스턴스와 함께 카프카 패키지를 실행할 수 있습니다.
```bash
bin/zookeeper-server-start.sh config/zookeeper.properties
```
실행한 터미널은 그대로 두고 새로운 터미널을 띄워 카프카 서버도 실행시킵니다.
```bash
bin/kafka-server-start.sh config/server.properties
```

## 토픽 만들기
그럼 다음으로 single partition과 하나의 replica를 가진 "test"라는 이름의 토픽을 만들겠습니다.
이전에 띄운 2개의 터미널을 그대로 둔채 새로운 터미널을 열어 아래 커맨드를 실행합니다.
```bash
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic test
```
이제 토픽이 잘 만들어졌는지 확인할 수 있습니다.
```bash
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
# test
```

## Producer에서 메세지 보내기
카프카는 파일이나 커멘드라인에서 input을 입력받아 카프카 클러스터로 메세지를 보낼 수 있습니다. 기본적으로 각 라인은 다른 메세지로 보내집니다.
Producer를 실행 후 몇몇 메세지를 콘솔에 입력해 서버로 보내도록 해보겠습니다.
```bash
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
# This is a message
# This is another message
```

## Consumer 시작하기
카프카는 커멘드라인 Consumer를 가지고 있어, standard out으로 메세지를 볼 수 있습니다.
```bash
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
# This is a message
# This is another message
```

여기서 한 발 더 나가서, 2개의 터미널을 열어 한 쪽은 Producer, 다른 한 쪽은 Consumer를 실행시키고, Producer 쪽 터미널에서 메세지를 입력하면 Consumer 쪽에서 메세지를 성공적으로 받는걸 확인 할 수 있습니다.


