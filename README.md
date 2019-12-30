# elastic-search

> Apache Lucene 기반의 JAVA 오픈소스 분산 검색엔진
> 거의 실시간으로 다량의 데이터를 저장, 검색, 분석
> 수평적인 구조, ES는 루씬을 중심으로 여러 기능을 추가해 제품화한 것

## ES vs RDB

> Index == Database
> Type == Table
> Document == Row
> Field == Column
> Mapping == Schema
>
> 1. ES는 역정규화 형태로 저장되고, JOIN은 불가능하다.
> (inverted index)
> 2. 대문자는 소문자로 변환되고, a, an, the 등 검색어로써 가치가 없는 단어를 제거한다.
> 
>
>> 의미 검색이 가능하다. -> 명사, 동사 등 구분이 가능하다.
>> 문서 분석 단계가 있다. -> 형태소(뜻을 가진 가장 작은 말의 단위), 품사(단어를 기능/형태/의미에 따라 나눈 것) 분석
>> "아버지가방에들어가신다." -> 아버지가(명사), 방에(격조사), 들어가신다.(동사)
>>
>> NY -> newyork 등 문서의 정확성이 높다.
>> NoSQL에 포함된다.


## 용어 정의

1. Cluster
>> 연결된 노드들의 집합

2. Node
>> 데이터를 색인하고 검색하는 하나의 단위 프로세스

3. Index
>> 검색의 최소 단위(Client 적으로), 샤드의 그룹

4. Shard
>> 검색의 최소 단위(System 적으로)
>> Primary Shard: 인덱스 생성 시 수를 결정
>> Replica Shard: PS의 복제본, 데이터 유실 방지


## Node의 역할

1. Master Node
>> 인덱스 생성, 삭제
>> 노드, 클러스터의 상태 확인
>> 데이터 할당 위치 결정

2. Data Node
>> 데이터와 관련된 CRUD, search, aggregation 작업 수행
>> IO / CPU, Memory 등의 자원을 많이 소모

3. Injest Node
>> 데이터 변환 등 Injest PipeLine을 실행하는 역할

4. Coordination only Node
>> 로드밸런서와 비슷한 역할


## 클러스터링 과정

> 클러스터 > 노드 > 샤드
> 하나의 노드가 다운되더라도 다른 노드에서 찾을 수 있도록 다른 노드에도 같은 샤드를 추가한다.
> 따라서 검색의 무결성을 유지하고, 검색 성능을 향상시킬 수 있다.


## REST API

> JSON 형식으로 데이터를 주고 받을 수 있다.
> 1. cURL 사용
> 2. Console Tool 사용




