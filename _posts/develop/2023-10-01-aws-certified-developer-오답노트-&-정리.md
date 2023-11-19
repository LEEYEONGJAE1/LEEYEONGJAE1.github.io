---
layout: post
develop: true
published: true
---
---
## IAM

IAM 사용자 그룹에는 다른 사용자 그룹이 포함될 수 **없다**.

---

## EC2

EC2 예약 가능 기간 : 1년 또는 3년

AMI는 다른 AZ에서 바로 사용할수 없다. (복사해서 사용가능)

### REGION과 AZ
![](https://d2908q01vomqb2.cloudfront.net/fc074d501302eb2b93e2554793fcaf50b3bf7291/2021/09/23/Figure-1.-An-example-system-that-transfers-data-across-AZs.png)

### EBS와 EFS
EBS는 같은 AZ내에서만 사용할수 있다.

같은 AZ내에서 하나의 EBS는 여러 인스턴스(EC2)에 연결될수 있다. 

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

---

## Elastic beanstalk

