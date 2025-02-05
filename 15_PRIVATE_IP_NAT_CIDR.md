# 사설 IP와 NAT, CIDR

## 사설 IP의 등장 배경
한정된 public IP 주소를 최대한 활용하기 위해 IP 주소를 분할해서 사용하고자 만든 IP 주소입니다.

IPv4 기준으로 최대 IP 개수는 약 43억 개입니다.

## 사설망 (Private Network)
- 사설망 내부는 외부망에서 통신할 수 없는 사설 IP로 구성됩니다.
- 외부로 통신할 때에는 public IP를 사용합니다.
- 보통 하나의 망은 사설 IP를 부여받은 기기들과 NAT 기능을 갖춘 Gateway로 구성됩니다.
- 인터넷을 통신할 때에는 각 public IP를 기준으로 통신하며, 사설 IP끼리는 서로 통신할 수 없습니다.
- 각각의 사설망은 공유기를 통해 라우팅됩니다.
- IPv6는 주소 개수가 많아, 사설망 개념이 따로 없습니다.

### **NAT (Network Address Translation)**
공인 IP (public ip)를 사설 IP로 바꿔주는, 즉 라우팅해주는 방법입니다.

### **Dynamic NAT**

하나의 공인 IP를 사설 IP pool에서 하나의 사설 IP를 선택하여 매칭합니다.

### **Static NAT**

- 하나의 공인 IP에 하나의 사설 IP를 매핑합니다.
- AWS Internet Gateway에서 사용하는 방식입니다.
  
### **PAT (Port Address Translation)**

- 많은 사설 IP를 하나의 공인 IP에 매핑합니다.
- NAT Gateway와 NAT Instance가 사용하는 방식입니다.

### **CIDR (Classless Inter-Domain Routing)**

- IP 주소 할당 및 라우팅 효율성을 향상시키기 위해 기존의 클래스 기반 주소 지정 방식(Class A, B, C 등)을 대체하는 기술입니다.
- IP 주소의 영역을 여러 네트워크 영역으로 나누기 위해 IP를 묶는 방식
- 여러 개의 사설망을 구축하기 위해 망을 나누는 방법
- CIDR Block : IP 주소의 집합 입니다.
- CIDR Notation (CIDR 표기법) : CIDR Block을 표시하는 방법으로, 네트워크 주소와 호스트 주소로 이루어져있습니다.
  - A.B.C.D/E 형식 (예: 192.168.1.0/24)
  - /24는 처음 24비트가 네트워크 주소임을 나타내며, 나머지 비트는 호스트 주소로 사용됩니다. (호스트 주소: 총 32개에서 네트워크 주소인 24를 뺀 8개)
  - A.B.C는 고정, D/E는 가변으로 IP주소의 범위를 나타낼 수 있습니다.
  - 예를들면, 192.168.1.0/24 는 192.168.1.0 부터 192.168.1.255 까지의 범위를 나타내는 표기입니다.
  - 호스트 주소 8이라, 2의 8재곱으로 256개의 호스트를 가지고 있어서 192.168.1.0~255 범위의 모든 IP주소이고, 네트워크 주소는 24.
  - 따라서 총 256개의 IP주소를 의미하게 됩니다.
- 따라서 CIDR은 하나의 IP주소가 아닌, 여러 IP주소를 포함하는 범위를 나타내는 형식입니다.

### **서브넷**
