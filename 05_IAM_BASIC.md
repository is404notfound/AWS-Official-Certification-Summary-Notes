# IAM (Identity and Access Management)

## 1. IAM 소개

IAM은 AWS와 리소스에 대한 액세스를 안전하게 관리할 수 있도록 지원하는 서비스입니다.  
AWS 사용자 및 그룹을 생성하고 관리하며, AWS 리소스에 대한 액세스를 허용하거나 거부할 수 있습니다.

### 주요 특징

- **AWS 계정 및 리소스 관리**:
  - 리소스, 사용자, 서비스에 대한 권한 제어
  - 서비스 사용을 위한 인증 정보 부여
  
- **사용자 생성 및 계정 보안 관리**:
  - 사용자의 패스워드 정책 관리(예: 일정 시간마다 패스워드 변경 요구 등)

- **다른 계정과의 리소스 공유**:
  - Facebook 로그인, Google 로그인 등 외부 인증 서비스와 통합 가능

- **로그인 주소 커스터마이징**:
  - 계정에 별명을 부여하여 로그인 주소를 생성할 수 있음

- **글로벌 서비스**:
  - IAM은 글로벌 서비스로, 리전별로 분리되지 않고 모든 리전에서 동일하게 관리됩니다.

---

## 2. IAM 구성 요소

### 1. 사용자 (User)

- AWS를 사용하는 유저 및 애플리케이션을 나타냅니다.
- 각각의 사용자에게 개별적인 인증 정보와 권한을 부여할 수 있습니다.

### 2. 그룹 (Group)

- 사용자의 집합입니다.
- 그룹 단위로 권한을 설정하여 여러 사용자에게 공통 권한을 부여할 수 있습니다.

### 3. 정책 (Policy)

- 사용자, 그룹, 역할(Role)에 대해 **무엇을 할 수 있는지**를 정의한 문서입니다.
- **JSON 형식**으로 작성됩니다.
- 정책을 통해 AWS 리소스에 대한 세부적인 권한 제어가 가능합니다.

### 4. 역할 (Role)

- AWS 리소스에 부여하여, AWS 리소스가 **무엇을 할 수 있는지**를 정의합니다.
- **주요 특징**:
  - 다른 사용자가 역할(Role)을 부여받아 사용할 수 있습니다.
  - 다른 자격 증명과의 신뢰 관계를 구축할 수 있습니다.
  - 역할을 변경하며 다양한 서비스 사용이 가능합니다.

---

## 3. 사용자의 종류

### 루트 사용자

- 결제 관리를 제외한 모든 권한을 가지고 있습니다.
- 관리 목적 이외에 다른 용도로 사용하지 않는 것을 권장
- 탈취 되었을 때 복구가 어려움 -> MFA를 설정하는 것을 권장
- MFA(Multi Factor Authentication): 일회용 패스워드 생성 후 로그인

### IAM 사용자

- IAM을 통해 생성해서 사용하는 사용자
- 한 사람 혹은 한 어플리케이션을 의미
- 설정 시 콘솔 로그인 권한 부여 가능
- 설정 시 AWS 서비스를 이용 가능
  - Access Key
  - Secret Access Key
- AdminAccess 권한을 부여하더라도 별도의 루트관리자의 설정 없이는 빌링 기능을 사용할 수 없음

---

## 4. IAM 자격 증명 보고서

- 계정의 모든 사용자와 암호, MFA 증명장치들의 증명 상태를 나열하는 보고서를 생성하고 다운로드 할 수 있다.
- 4시간에 한번씩 생성 가능
- AWS 콘솔, CLI, API에서 생성 요청 및 다운로드 가능
- 포함되는 정보
  - **암호**
    - 암호의 활성화 여부
    - 마지막으로 사용된 시간
    - 마지막으로 변경된 시간
    - 언제 변경되어야 하는지
  - **엑세스 키**
    - 엑세스 키 활성화 여부
    - 마지막으로 사용된 시간
    - 마지막으로 변경된 시간
    - 어떤 서비스에 마지막으로 사용 되었는지
  - 기타
    - MFA 사용 여부
    - 사용자 생성 시간


---

## 5. IAM 모범 사용 사례

- 루트 사용자는 사용하지 않기
- 불필요한 사용자는 만들지 않기 (관리가 어려워 짐)
- 가능하면 그룹과 정책을 사용해서 유저를 관리하기
- 최소한의 권한만을 허용하는 습관을 들이기
- MFA를 활성화 하기
- AccessKey 대신 역할을 활용하기 (가능하면 AccessKey 사용하지 않기)
- IAM 자격 증명 보고서(Credential Report)를 활용해서 평소에 계정 상태들을 확인하기
