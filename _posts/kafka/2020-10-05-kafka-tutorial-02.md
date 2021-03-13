---
title: "Kafka 튜토리얼 02 - multi broker 클러스터 셋업"
excerpt: "Kafka 설치"

categories:
  - Kafka tutorial
tags:
  - kafka
  - 카프카
  - install
  - 설치
  - tutorial
  - 튜토리얼
  - broker
  - setup
last_modified_at: 2020-10-05T08:06:00-05:00
---

## multi-broker cluster 셋업하기
현재까지 우리는 single cluster만 실행시켜봤습니다. 이것만으로는 재미가 없네요. 

카프카에서 싱글 broker는 사이즈 하나의 클러스터이기 때문에 여러 개의 brokers들을 실행하는 것과 큰 차이가 없습니다. 하지만 한 번 체험해 보기 위해, 우리의 클러스터를 3개의 노드들로 늘려보죠!

먼저 각 brokers들의 config 파일을 만듭니다. (Windows 경우엔 copy 명령어를 이용해 주세요)
```bash
cp config/server.properties config/server-1.properties
cp config/server.properties config/server-2.properties
```

이제 이 새 파일들을 수정해보죠.
server-1.properties 파일로 가서 안에 존재하는 내용을 아래 내용으로 바꿔 줍니다.
```bash
broker.id=1
# listeners 는 코멘트 인이 되어있으므로 코멘트 아웃을 하면 됩니다.
listeners=PLAINTEXT://:9093
log.dirs=/tmp/kafka-logs-1
```
server-2.properties도 마찬가지입니다.
```bash
broker.id=2
listeners=PLAINTEXT://:9094
log.dirs=/tmp/kafka-logs-2
```

broker id는 유니크한 속성으로 cluster 안에 각 노드의 영구적인 이름입니다. 우리는 같은 머신에서 실행시키고 있고 서로 다른 데이터의 오버라이트를 막기위해 포트와 로그 디렉토리를 바꿉니다.

우리는 이미 Zookeeper를 가지고 있고 single node를 실행시켰기 때문에 우리는 두 개의 새로운 노드를 실행시키기만 하면 됩니다.
```bash
bin/kafka-server-start.sh config/server-1.properties &
bin/kafka-server-start.sh config/server-2.properties &
```

이제 3개의 replication-factor과 함께 새로운 토픽을 만듭니다.
```bash
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 1 --topic my-replicated-topic
```

이제 describe 옵션을 통해 우리의 토픽 정보를 볼 수 있습니다.
```bash
bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic my-replicated-topic
#Topic:my-replicated-topic       PartitionCount:1        ReplicationFactor:3     Configs:segment.bytes=1073741824
#        Topic: my-replicated-topic      Partition: 0    Leader: 0       Replicas: 1,0,2 Isr: 0
```
첫 줄은 모든 파티션들의 정보를 보여주고, 그 다음 각 각 라인은 파티션 하나에 대한 정보를 보여줍니다.
우리는 my-replicated-topic 토픽에 대해 하나의 파티션만 가지고 있으므로, 한 라인만 보여집니다.

* leader : 리더는 주어진 파티션에서 모든 읽기와 쓰기를 담당하는 노드입니다. 각 노드는 파티션 가운데 랜덤하게 리더로 선택됩니다.
* replicas : 레플리카는 노드들의 리스트로, 파티션을 위해 로그를 복제합니다. 여기서 노드가 리더이든 아니든, 살아있던 아니든 관계없이 복제가 됩니다. 
* isr :  isr은 비동기 레플리카 셋입니다. 이건 현재 살아있고, 리더를 따라잡힌 레플리카 리스트들의 부분집합입니다.

해당 문서는 카프카 공식 홈페이지를 참고했습니다. [공식 홈페이지](https://kafka.apache.org/22/documentation.html#quickstart)