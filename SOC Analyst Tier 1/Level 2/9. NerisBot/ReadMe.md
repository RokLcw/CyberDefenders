# NerisBot

## 목차

[Questions 1](#q1)

[Questions 2](#q2)

[Questions 3](#q3)

[Questions 4](#q4)

[Questions 5](#q5)

# Scenario
Unusual network activity has been detected within a university environment, indicating potential malicious intent. These anomalies, observed six hours ago, suggest the presence of command and control (C2) communications and other harmful behaviors within the network.

Your team has been tasked with analyzing recent network traffic logs to investigate the scope and impact of these activities. The investigation aims to identify command and control servers and uncover malicious interactions.

대학 환경에서 비정상적인 네트워크 활동이 감지되었으며, 이는 잠재적인 악의적 의도를 시사합니다. 6시간 전에 관찰된 이러한 이상 징후는 네트워크 내에서 명령 및 제어(C2) 통신 및 기타 유해 행위가 존재함을 시사합니다.

귀하의 팀은 최근 네트워크 트래픽 로그를 분석하여 이러한 활동의 범위와 영향을 조사하는 임무를 맡았습니다. 이 조사의 목표는 명령 및 제어 서버를 식별하고 악의적인 상호 작용을 적발하는 것입니다.

# 문제 파일
네트워크 트래픽을 모니터링하고 분석할 수 있는 수리카타(Suricata) 앱이 설치되어 있는 머신이 주어진다.

# 개념 정리

# Questions

## Q1
During the investigation of network traffic, unusual patterns of activity were observed in Suricata logs, suggesting potential unauthorized access. One external IP address initiated access attempts and was later seen downloading a suspicious executable file. This activity strongly indicates the origin of the attack.

What is the IP address from which the initial unauthorized access originated?

네트워크 트래픽 조사 중 수리카타 로그에서 비정상적인 활동 패턴이 관찰되었으며, 이는 무단 접근 가능성을 시사합니다. 외부 IP 주소 하나에서 접근 시도가 시작되었고, 이후 의심스러운 실행 파일을 다운로드하는 것이 확인되었습니다. 이러한 활동은 공격의 발원지를 강력하게 시사합니다.

최초 무단 접근이 발생한 IP 주소는 무엇입니까?

### Answer

### 분석