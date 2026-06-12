# 🌏 woowa-network

## 👀 App
- [Goto Roomescape](http://43.202.2.142:8080)

## ❓ Keywords

| 개념 | 한 줄 정리 |
|---|---|
| AWS Region | AWS 데이터센터들이 위치한 지리적 묶음 |
| VPC | AWS 안에서 내가 따로 만든 전용 네트워크 공간 |
| Subnet | VPC를 더 작게 나눈 네트워크 구역 |
| Amazon Route 53 | 도메인 이름을 IP 주소로 연결해주는 DNS 서비스 |
| Application Process | EC2 안에서 실제로 실행 중인 애플리케이션 프로그램 |
| Browser | 사용자가 서비스를 요청하고 응답을 받는 클라이언트 프로그램 |
| Instance | AWS에서 빌려 쓰는 가상 서버 |
| ENI | EC2에 연결되는 가상 네트워크 카드 |
| Internet Gateway | VPC가 인터넷과 통신할 수 있게 해주는 출입문 |
| Route Table | 목적지 IP에 따라 트래픽이 어디로 가야 하는지 정하는 경로표 |
| Security Group | EC2나 ENI 앞에서 인바운드·아웃바운드 트래픽을 제어하는 방화벽 |

```mermaid
architecture-beta
  group browser(cloud)[Browser]
  group aws_region(cloud)[AWS Region]
  group vpc(cloud)[VPC] in aws_region
  group subnet(cloud)[Public Subnet] in vpc
  group instance(server)[EC2 Instance] in subnet
  
  service eni(internet)[ENI] in instance
  service app(server)[Application] in instance
  service sg(disk)[Security Group] in subnet
  service rt(disk)[Route Table] in vpc
  service igw(internet)[Internet Gateway] in vpc
  service route53(cloud)[Route 53] in aws_region
  
  service browser_svc(internet)[Browser Service] in browser
  
  browser_svc{group}:R --> L:route53{group}
  route53:R --> L:igw
  igw:B --> T:rt
  rt:B --> T:sg
  sg:R --> L:eni
  eni:R --> L:app
```

## 🗒️ passports

### request

| request | response |
|---|---|
| <img width="1082" height="766" alt="스크린샷 2026-06-11 16 45 14" src="https://github.com/user-attachments/assets/29324731-97c1-4a0c-8794-aafad4466432" /> | <img width="1082" height="766" alt="스크린샷 2026-06-11 16 45 14" src="https://github.com/user-attachments/assets/29324731-97c1-4a0c-8794-aafad4466432" /> |
