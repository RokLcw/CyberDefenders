# PsExec Hunt

## 목차

[Questions 1](#q1)

[Questions 2](#q2)

[Questions 3](#q3)

[Questions 4](#q4)

[Questions 5](#q5)

[Questions 6](#q6)

[Questions 7](#q7)

# Scenario
An alert from the Intrusion Detection System (IDS) flagged suspicious lateral movement activity involving PsExec. This indicates potential unauthorized access and movement across the network. As a SOC Analyst, your task is to investigate the provided PCAP file to trace the attacker’s activities. Identify their entry point, the machines targeted, the extent of the breach, and any critical indicators that reveal their tactics and objectives within the compromised environment.

침입 탐지 시스템(IDS)의 경보에서 PsExec과 관련된 의심스러운 측면 이동 활동이 감지되었습니다. 이는 네트워크 전반에 걸쳐 무단 접근 및 이동 가능성이 있음을 나타냅니다. SOC 분석가의 임무는 제공된 PCAP 파일을 조사하여 공격자의 활동을 추적하는 것입니다. 공격자의 진입점, 대상 기기, 침해 범위, 그리고 침해된 환경 내에서 공격자의 전술과 목표를 드러내는 주요 지표를 파악해야 합니다.

# 문제 파일
pcapng 파일이 주어진다.

# 개념 정리

# Questions

## Q1
To effectively trace the attacker's activities within our network, can you identify the IP address of the machine from which the attacker initially gained access?

네트워크 내에서 공격자의 활동을 효과적으로 추적하려면 공격자가 처음 접근한 컴퓨터의 IP 주소를 식별할 수 있습니까?

### Answer

### 분석