---
title: "couchbase server"
date: 2019-11-16 21:50:00
categories: couchbase
---

### couchbase server 

카우치베이스 클러스터의 각 서버는 해시 주소 나눠지며, 애플리케이션에서 카우치베이스 클라이언트 라이브러리는 어떤 ip 주소가 어떤 해시값 범위를 가지고 있는지 보여주는 맵을 가지고 있다. -> 문서 접근시 문서의 위치를 알기 위해 다른 곳을 거칠 필요 없이 해당 노드애 바로 접근할 수 있다는....
각 문서의 위치는 문서의 버킷과 키의 해시값을 가지고 해당 해시값을 담당하는 서버에 배치된다.  

각 문서는 하나의 활성문서가 존재한다. 모든 일기, 쓰기 작업은 하나의 활성문서에만 이루어진다.  
이 의미는, 클러스터 내에서 다른 곳으로 복제하기 위한 쓰기 작업이 없으므로, 문서의 일관성에 대해 걱정할 필요가 없다는 뜻이다.  

각 문서의 복제는 자동으로 이루어지고, 이는 활성문서로부터 독립된 서버에 저장된다. 카우치베이스 서버에서 복제는 전체 서버 레벨이 아닌 문서레벨에서 발생한다. 이는 각각의 노드는 다른 데이터 셋을 가지고 있고, 복제는 클러스터 전체에 분산된다는 의미이다.  

단일 장애 지점이 없으며 클러스터에 서버를 추가하여 대규모 데이터 셋으로 쉽게 확장 할 수 있다. 전체 데이터 셋이 모든 단일 서버에 맞지 않아도된다.



### caching

Couchbase 서버는 관리 캐시 가 내장되어 있다. 요청할 때마다 Couchbase 서버는 필요한 문서의 캐시를 검사한다. 문서가 캐시에 없으면 디스크에서 문서를로드 한 다음 사용자에게 제공한다.  

모든 쓰기는 캐시에 저장되며 요청에서 디스크에 쓰거나 다른 서버로 복제되는 시점을 조정할 수 있다.  

대부분의 키-값 요청은 1 밀리 초 미만이다.



##### ref
https://www.couchbase.com/couchbase-vs-couchdb
