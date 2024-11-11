1. **AWS history**
  - 2002년 Amazon.com의 부속 기능으로 출발
  - 2006년 첫번째 클라우드 제품 출시 (S3/EC2 등)
  - 2009년 VPC 발표
  - 2013년 자격증 도입
  - 2020년 53조 돌파, 꾸준히 성장중

2. AWS Service의 리전, 가용영역, 엣지로케
  - AWS의 서비스는 전세계적으로 여러개의 걱 지역별 리전으로 나누어져 있다
  - **리전** 
    - AWS의 서비스가 제공되는 서버(데이터 센터)의 물리적 위치로, 각 리전에는 고유의 코드가 부여된다
    - 각 리전별로 사용이 가능한 서비스가 다르다. (만약, 국내에서 사용할 수 없는 서비스를 사용해야 하는 경우엔 리전코드를 바꿔서 접근하면 된다)
    - 서울 리전 고유코드 : ap-northeast-2
    - 리전 코드 AP에 속해있는 나라 : 중국, 호주 등
    - 미국 동부 리전: us-east-1 (AWS의 모든 서비스가 가장 처음 릴리즈 되는 리전으로, 가장 중요한 리전)
  - **리전을 선택할 때 고려할 점**
    - 지연 속도 (내가 속해있는 국가의 리전을 사용하는 게 가장 빠름)
    - 법률(데이터 제공, 서비스 제공 관련 정책들)
    - 사용 가능한 AWS 서비스

  - **가용 영역**(Availability Zone)
    - 리전의 하부 단위로, 하나의 리전은 반드시 2개 이상의 가용영역으로 구성
    - 가용영역은 하나 이상의 데이터센터로 구성
    - 리전간의 연결은 매우 빠른 전용 네트워크로 연결된다
    - 여러 재헤에 대한 대비 및 보안을 위해 가용영역은 반드시 물리적으로 일정 km이상 떨어져있으며, 동시에 서로 100km이내의 거리에 위치한다
    - 보안 및 트레픽 몰림을 방지하기 위해, AWS의 계정주가 선택했던 각각의 가용영역의 코드(AZ-A, AZ-B, AZ-C 등)는 문자 코드가 같다 하더라도 실제 배정되는 데이터센터의 위치와 다르다. 
      예시: 계정 test1의 AZ-A(가용영역-A)는 계정 test2와 AZ-A와 다른 위치다(랜덤 배정)

  - ** 리전과 가용영역 별로 구분한 WS서비스 **
    - 리전이 존재하지 않은 서비스 : IAM / Amazon Cloud Front
    - 리전에 속해있는 서비스 : VPC, S3
    - 리전 내 가용영역A에 속해있는 서비스: RDS
    - 리전 내 가용영역B에 속해있는 서비스: EC2
