Data Lifecycle Engineer을 위한 지식을 학습하고 꺼내쓰기 위한 공간입니다.
변화하지 않는 것을 이해할 수 있도록 기본에 충실하되, 새로운 기술이 등장했을 때 그 흐름에 동참하기 위해서 지속적으로 업데이트합니다.

단순한 도구 사용법이 아닌, 데이터 도구들을 평가하는 방법과 데이터 엔지니어링 수명 주기 전반에 걸쳐 이 도구들이 어떻게 조합되는지를 이해하는 것에 초점을 둡니다.

# 01_Programming and Scripting 

## Python
- 데이터 추출, 전처리 및 ETL 작업을 위한 코드를 작성하고 디버깅 및 최적화하기 위한 Language
- 많은 엔지니어링 도구가 파이썬으로 작성되거나 파이썬 API를 가진다. 
### DataStructure and Algorithms

### Pandas

### Flask API 설계
Flask는 쉽고 빠르게 API를 만들 수 있는 Python Library
Port, HTTP 리퀘스트, 커맨드 라인 등의 기본 개념을 실제로 API를 만들어보면서 학습

### Test Driven Development(TDD)
Unit Test vs Integratiopn Test


## SQL
- 전처리한 데이터를 데이터베이스에 적재, 데이터 조작 및 분석을 위한 쿼리 Language
- 데이터베이스와 데이터레이크의 가장 일반적인 인터페이스 
## Linux
### OS
### Bash
- Window OS에서는 Powershell
- 리눅스 운영체제용 명령형 인터페이스. 스크립트를 작성하거나 OS 명령을 수행해야 할 때, 배시 명령어를 알고 CLI 사용에 능숙하면 생산성과 워크플로가 대폭 향상함. 
- 데이터 엔지니어는 데이터 파이프라인에서 파일 처리를 위해 awk or sed와 같은 명령행 도구를 자주 사용함
- 오케스트레이션 프레임워크에서 bash 명령어를 호출하기도 함.

## JVM Language
Scala, Java

# 02_Database
데이터 모델링 및 데이터베이스 설계
- 데이터 정규화, 스키마 설계 및 데이터 웨어하우징 개념 이해
- 다양한 Usecase에 맞게 효율적이고 확장 가능한 데이터베이스 스키마 설계

## Relational Database
## NoSQL

# 03_Data Pipeline
## 1. Data Engineering lifecycle
### 1) Data Generation
- 로그 데이터, 센서 데이터, 트랜잭션 데이터 등 다양한 Source System으로부터 추출되는 raw data 특징 파악하기

### 2) Data Storage
- 수집된 데이터를 영구적으로 저장하는 단계.
- 데이터베이스, 데이터 웨어하우스, 데이터 레이크 등 스토리지 솔루션 선택이 중요하다.(trade-off)
- 스토리지와 다른 수명 주기 간의 교차점 : 저장은 데이터 파이프라인의 여러 위치에서 발생한다. 즉, 전체 데이터 엔지니어링 수명 주기에 걸쳐 실행된다.

### 3) Data Ingestion
- 원천 시스템 및 데이터 저장 방법을 이해한 뒤에, 원천 시스템에서 데이터를 수집하는 단계
- 데이터 수집 방법 : 배치 vs 스트리밍
- 푸시 패러다임 vs 풀 패러다임
  
### 4) Data Transformation
- 수집된 데이터를 필요한 형식으로 변환하거나 조작하는 단계

### 5) Data Serving
- 변환된 데이터를 분석, 시각화, 응용 프로그램 등에 제공하는 단계

## 2. Data Architecture
- 데이터 아키텍처가 데이터 엔지니어링 수명 주기에 어떻게 부합하는지
- 우수한 데이터 아키텍처를 만드는 요소는 무엇인지
- 데이터 아키텍처의 예 : 데이터 웨어하우스, 데이터 레이크 등
- 모든 아키텍처에 내재된 트레이드오프를 이해하는 것이 중요하다. 그 과정에서 조직의 고유한 요구사항에 대응하는 아키텍처를 설계하기 위한 통찰력이 생길 것.
## Data Warehouse
- **ETL**이 포함된 기본 데이터 웨어하우스
-   원천 시스템에서 데이터를 가져오는 추출
    -> 데이터를 정리하고 표준화해 고도로 모델링된 형태로 비즈니스로직을 구성하고 적용하는 데이터 모델링 및 변환
    -> 데이터가 데이터 웨어하우스 대상 DBMS에 푸시되고, 사용자의 요구에 따라 해당 니즈를 충족하는 여러 데이터 마트에 적재
- **ELT**
-    데이터 웨어하우스에 원천 데이터가 row form으로 스테이징되고, 변환은 외부 시스템을 사용하는 대신, 데이터 웨어하우스에서 직접 처리됨.
-   이는 클라우드에서 데이터 웨어하우스와 데이터 처리 도구의 방대한 계산 능력을 활용하려는 것으로, 데이터는 batch 처리되며, 변환된 출력은 분석을 위해 테이블 및 뷰에 기록됨.  
## Cloud Networking and Architecture
- 레드시프트, 구글 빅쿼리, 스노우플레이크 등
## Data Lake
- 매우 저렴한 스토리지 비용과 사실상 무제한 스토리지 용량을 갖춘 클라우드 기반 객체 스토리지로 옮겨가면서,
- 스토리지와 컴퓨팅이 긴밀하게 연결된 단일 데이터 웨어하우스에 의존하는 대신, 모든 크기의 유형과 방대한 데이터를 저장할 수 있다.
- 맵리듀스, 스파크, 레이, 프레스토, 하이브 등 원하는 데이터 처리 기술을 선택해 작업을 수행할 수 있다. 
## 람다 아키덱처
- 배치, 스트리밍 및 서빙 등의 시스템이 서로 독립적으로 작동. 원천 시스템은 이상적으로 변경할 수 없고 추가만 가능하며, 데이터를 처리할 때 스트림과 배치라는 두 목적지로 전송함.


## 오케스트레이션
### Airflow
### Container : Docker, k8s

# 04_Data Warehousing

===

# Materials

[도서]
- <Fundamentals of Data Engineering, Reis Joe, Housley Matt>
- <빅데이터를 지탱하는 기술, 니시다 케이스케>
- <실무로 배우는 빅데이터 기술, 김강원>
- <The Data Warehouse Toolkit, Ralph Kimball>
- <Data Pipelines with Apache Airflow, Bas P. Harenslak, Julian Rutger de Ruiter>
- <이것이 취업을 위한 코딩테스드다 with 파이썬, 나동빈>
- <CS 지식의 정석, 주홍철>


[강의]
- [Learn Flask for Python - Full tutorial](https://www.youtube.com/watch?v=Z1RJmh_OqeA)
- [Data Warehouse Fundamentals for Beginners](https://www.udemy.com/course/data-warehouse-fundamentals-for-beginners/?ranMID=39197&ranEAID=GjbDpcHcs4w&ranSiteID=GjbDpcHcs4w-8xplSp9w_fkfgoR0YXaG2A&LSNPUBID=GjbDpcHcs4w&utm_source=aff-campaign&utm_medium=udemyads&couponCode=KEEPLEARNING)
- [Unit Testing and Test Driven Development in Python](https://www.udemy.com/course/unit-testing-and-tdd-in-python/?ranMID=39197&ranEAID=GjbDpcHcs4w&ranSiteID=GjbDpcHcs4w-KudpdnnpEA3QyjbxvMhcRg&LSNPUBID=GjbDpcHcs4w&utm_source=aff-campaign&utm_medium=udemyads&couponCode=KEEPLEARNING)
- [Database Systems Full University Course](https://youtu.be/4cWkVbC2bNE)
- [IBM Data Engineering Professional Certificate](https://www.coursera.org/professional-certificates/ibm-data-engineer)
- [AWS Certified Solutions Architect Associate](https://www.udemy.com/course/best-aws-certified-solutions-architect-associate/?couponCode=KEEPLEARNING)
- [초보자를 위한 BigQuery(SQL) 입문](https://www.inflearn.com/course/%EC%B4%88%EB%B3%B4%EC%9E%90%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%B9%85%EC%BF%BC%EB%A6%AC-sql-%EC%9E%85%EB%AC%B8)
- [Preparing for Google Cloud Certification: Cloud Data Engineer](https://www.coursera.org/professional-certificates/gcp-data-engineering)
