# SQL
# Python, Library(pandas, NumPy, sci-kit learn, Tensorflow, PySpark)
# Commends line : Linux
1. 원격 서버 작업: 데이터 엔지니어는 종종 원격 서버에서 작업합니다. 원격으로 서버에 액세스하여 파일을 이동하고 로그를 검색하고 버전을 관리하는 데 필요한 강력한 도구입니다.

2. 파일 이동 및 검색: 파일을 쉽게 이동하고 검색할 수 있습니다. 이것은 ETL(Extract Transform Load) 파이프라인을 구축할 때 매우 유용합니다. 데이터 엔지니어는 종종 데이터를 추출하고 변환한 다음 로드해야 하므로, 이러한 프로세스를 간편하게 만들어줍니다.

3. 개발자 생산성 향상: 명령은 자동화 및 스크립팅에 쉽게 사용할 수 있으며, 작업을 자동화하여 반복적인 작업을 줄일 수 있습니다.

# Data-Engineering

## Data architecture : Data lake vs Data lakehouse vs Data Warehouse
- 데이터 웨어하우스 : 구조화된 데이터만
- 데이터 레이크 : 구조화, 반구조화, 비고주화(원시) 데이터, 확장성(저장 자체를 object storage로 하기 때문)
- 데이터 레이크하우스 : 다양한 형식의 데이터를 저장하면서도 구조화된 데이터를 분석하고 쿼리할 수 있는 기능을 제공, 확장성(저장 자체를 object storage로 하기 때문)

## TCO(Total Cost of Ownership)을 고려한 데이터 처리 및 분석 플랫폼 구축
### Decoupling Compute and Storage

이러한 데이터 아키텍처는 데이터 처리 및 분석을 위해 필요한 컴퓨팅 리소스와 데이터를 저장하는 스토리지 리소스를 분리하는 개념. 
이는 필요한 경우에만 컴퓨팅 리소스를 확장하고, 데이터를 필요한 만큼 저장할 수 있도록 한다.

Amazon EC2 인스턴스를 사용하여 Hadoop 클러스터를 구성하는 경우, EC2 인스턴스는 컴퓨팅 리소스를 제공하고, Hadoop 클러스터의 노드 역할을 수행. 
이 때 클러스터의 데이터는 일반적으로 Hadoop Distributed File System (HDFS)에 저장되며, 이는 하둡 클러스터 내에서 데이터를 분산하여 저장하는 역할을 한다.

따라서, 필요하지 않은 데이터를 온프레미스(기업의 자체적인 데이터 센터나 서버를 보유하고 운영하는 것, 즉 클라우드 서비스가 아닌 내부 infra structure)나 하이브리드된 저장소에 저장하는 것은 "컴퓨팅과 저장소 분리" 아키텍처의 일환. 
이렇게 하면 필요한 경우에만 해당 데이터를 Hadoop 클러스터로 이동하여 분석할 수 있으며, 그렇지 않은 경우에는 Amazon S3에서 내려서 비용을 절감할 수 있습니다.

이러한 구성은 비용 효율성과 성능 향상을 동시에 실현할 수 있는 장점을 제공하며, 컴퓨팅 리소스와 스토리지 리소스를 효율적으로 활용할 수 있다. (TCO를 고려한 플랫폼)

### Elastic spot instance 고려
- EC2(amazon Elastic Compute Cloud)의 유휴자원을 Availability Zone 별로 경매를 통해 이용
- 빅데이터 분석, 배치작업, Stateless web, 이미지 렌더링, 대량 병렬 계산 등에서 활용
- spot fleet : 인스턴스(가상 컴퓨팅 환경) 가용성 유지를 위한 옵션
- spot block : 스팟 인스턴스를 일정 기간동안 스팟 인스턴스를 계속해서(1-6h)사용할 수 있는 옵션으로 지속적인 워크로드가 필요할 때 활용

### HDFS(Hadoop Distributed File system)로 S3(Object Storage)를 사용했을 때의 장점
- hadoop :  대량의 데이터를 처리하기 위한 오픈소스 프레임워크, HDFS는 하둡에서 사용되는 파일 시스템
- 왜 온프레미스가 아닌 클라우드 환경에서 데이터를 저장하는 것이 더 낫나?
- Compute node, data node를 구분해서 운영 가능
- cluster을 종료 후에 다시 cluster을 구성해도 기존 데이터를 읽을 수 있다.
- hdfs 확장에 대해 신경을 쓰지 않아도 됨

## Data Pipeline Architecture (AWS)
1. Communication : 데이터적 요구사항 분석(Use Case)과 데이터 선정 
2. Data 수집 (Amazon Kinesis Streams, Amazon API Gateway, Amazon Kinesis Firehouse, Lambda function)
3. Data 전처리 및 저장 (AWS Glue, Amazon S3, Amazon EMR)
 - S3 Data Lake :
    batch-Processing engine : spark - aws EMR, DMS  
    stream-Processing engine : Spark Streaming - aws kinesis Analytics
 - Serving Data Store : Amazon ES, Amazon DynamoDB, Amazon RDS, Amazon Redshift
 - Data Cataloging(AWS Glue) : S3에 데이터를 저장할 때 메타시스템 관리
4. Data 시각화, 분석 (Amazon Athena, Apache Zepplin, tableau, periscope Data, Superset)
    

