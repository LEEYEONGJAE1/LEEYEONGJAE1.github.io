---
layout: post
develop: true
published: true
---
---
## IAM
IAM 사용자 그룹에는 다른 사용자 그룹이 포함될 수 **없다**.

Trust Policy - A JSON policy document in which you define the principals that you trust to assume the role. A role trust policy is a required resource-based policy that is attached to a role in IAM. The principals that you can specify in the trust policy include users, roles, accounts, and services.

---

## EC2
EC2 예약 가능 기간 : 1년 또는 3년

AMI는 다른 AZ에서 바로 사용할수 없다. (복사해서 사용가능)

ec2 AWS CLI command line option > Env variable > CLI creds file .aws/credentials > CLI config file (.aws/config) > IAM role attached to ECS task definition > ec2 instance profile.

to create a new EC2 instance using the AWS CLI, you would typically use the aws ec2 run-instances command, providing the necessary parameters such as the AMI ID, instance type, security groups, and key pair, among others.

### REGION과 AZ
![](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2021/09/23/Figure-1.-An-example-system-that-transfers-data-across-AZs.png)

### EBS와 EFS
EBS는 같은 AZ내에서만 사용할수 있다.

같은 AZ내에서 하나의 EBS는 여러 인스턴스(EC2)에 연결될수 있다. 

---

## S3

### Cloudfront

Cloudfront functions are just within Cloudfront, hence, they DONT HAVE NETWORK ACCESS. 

---

## ELB
SNI를 사용하면 동일한 수신기에서 각각 자체 SSL 인증서가 있는 여러 HTTPS 애플리케이션을 노출할 수 있다.

---

## RDS
암호화 되지 않은 RDS에서는 암호화된 읽기전용 복제본을 생성할수 없다. 

15개의 읽기 전용 복제본 생성 가능

---

## ElastiCache
Amazon ElastiCache는 AWS 클라우드상의 분산 인 메모리 캐시 환경을 손쉽게 설정 및 관리하고 및 확장할 수 있습니다. 이 서비스는 분산 캐시 환경의 배포 및 관리와 관련된 복잡성을 제거하면서 고성능, 크기 조정 가능 및 비용 효율적인 인 메모리 캐시를 제공합니다. ElastiCache는 Redis 및 Memcached 엔진과 호환됩니다.

Memcached와 Redis 중에서 결정할 때 고려해야 할 몇 가지 질문은 다음과 같습니다. 데이터베이스 오프로드와 같은 객체 캐싱이 주요 목표입니까? 그렇다면 Memcached를 사용하세요.

---

## Lambda
Whenever you see "to make deployment package smaller" -----> Layers

---

## Elastic beanstalk
구성 파일은 .ebextensions라는 폴더에 배치하고 애플리케이션 소스 번들에 배포하는 .config 파일 확장자를 가진 YAML 또는 JSON 형식의 문서입니다.

---
## Cloudformation
To include objects defined by the AWS Serverless Application Model (SAM) in an AWS CloudFormation template, in addition to Resources, what section MUST be included in the document root? -> Transform

---
## SAM (Serverless Application Model)
YAML에서 서버리스 리소스를 정의하기 위해 권장되는 AWS 서비스는 AWS Serverless Application Model(AWS SAM)입니다. AWS SAM은 AWS CloudFormation을 확장하여 서버리스 애플리케이션에 필요한 Amazon API Gateway API, AWS Lambda 함수 및 Amazon DynamoDB 테이블을 정의하는 단순화된 방법을 제공하는 오픈 소스 프레임워크입니다. YAML 템플릿에서 서버리스 리소스를 정의한 다음 AWS SAM CLI를 사용하여 애플리케이션을 패키징하고 배포할 수 있습니다. AWS CloudFormation 서버리스 내장 함수를 사용하여 YAML에서 서버리스 리소스를 정의할 수도 있지만 AWS SAM에 비해 몇 가지 제한 사항이 있습니다. 

AWS Elastic Beanstalk는 서버리스 전용이 아닌 PaaS(Platform as a Service)인 반면, AWS CDK(AWS Cloud Development Kit)는 TypeScript, Python 및 Java와 같은 친숙한 프로그래밍 언어를 사용하여 정의하는 YAML 기반 템플릿의 대안입니다.

---

## Cloudwatch
cloudwatch notification -> 항상 SNS

---
## Cognito
Amazon Cognito의 두 가지 주요 구성 요소는 사용자 풀과 자격 증명 풀입니다. 자격 증명 풀은 사용자에게 다른 AWS 서비스에 대한 액세스 권한을 부여하는 AWS 자격 증명을 제공합니다. 사용자 풀의 사용자가 AWS 리소스에 액세스할 수 있도록 하려면 사용자 풀 토큰을 AWS 자격 증명과 교환하도록 자격 증명 풀을 구성할 수 있습니다.

User pool only *authenticates* however identity pool *authorizes*.

---

## Kinesis
Amazon Kinesis는 모든 규모의 스트리밍 데이터를 비용 효율적으로 처리하고 분석하는 완전관리형 서비스입니다. Kinesis를 사용하면 기계 학습, 분석 및 기타 애플리케이션을 위해 비디오, 오디오, 애플리케이션 로그, 웹 사이트 클릭스트림 및 IoT 원격 측정 데이터와 같은 실시간 데이터를 수집할 수 있습니다.

### Kinesis Data Stream
Amazon Kinesis Data Streams는 규모와 관계없이 데이터 스트림을 간편하게 캡처, 처리 및 저장할 수 있는 서버리스 스트리밍 데이터 서비스입니다.

### Kinesis Data Firehose
Amazon Kinesis Data Firehose는 스트리밍 데이터를 안정적으로 캡처하고 전환하여 데이터 레이크, 데이터 스토어, 분석 서비스에 전달하는 추출, 전환, 적재(ETL) 서비스입니다.

---
## CloudTrail
Who to blame? CLOUD TRAIL