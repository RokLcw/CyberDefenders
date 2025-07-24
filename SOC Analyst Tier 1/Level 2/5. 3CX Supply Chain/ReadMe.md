# 3CX Supply Chain

## 목차

[Questions 1](#q1)

[Questions 2](#q2)

[Questions 3](#q3)

[Questions 4](#q4)

[Questions 5](#q5)

[Questions 6](#q6)

[Questions 7](#q7)

[Questions 8](#q8)

[Questions 9](#q9)

# Scenario
A large multinational corporation heavily relies on the 3CX software for phone communication, making it a critical component of their business operations. After a recent update to the 3CX Desktop App, antivirus alerts flag sporadic instances of the software being wiped from some workstations while others remain unaffected. Dismissing this as a false positive, the IT team overlooks the alerts, only to notice degraded performance and strange network traffic to unknown servers. Employees report issues with the 3CX app, and the IT security team identifies unusual communication patterns linked to recent software updates.

As the threat intelligence analyst, it's your responsibility to examine this possible supply chain attack. Your objectives are to uncover how the attackers compromised the 3CX app, identify the potential threat actor involved, and assess the overall extent of the incident. 

한 대형 다국적 기업은 전화 통신에 3CX 소프트웨어를 크게 의존하고 있어 비즈니스 운영의 핵심 요소로 자리 잡았습니다. 최근 3CX 데스크톱 앱 업데이트 이후, 바이러스 백신 알림에서 일부 워크스테이션에서는 소프트웨어가 삭제되는 반면 다른 워크스테이션에서는 삭제되지 않는 현상이 산발적으로 나타납니다. IT 팀은 이를 오탐으로 간주하고 알림을 무시하다가 성능 저하와 알 수 없는 서버로의 비정상적인 네트워크 트래픽을 발견했습니다. 직원들은 3CX 앱 관련 문제를 보고했고, IT 보안 팀은 최근 소프트웨어 업데이트와 관련된 비정상적인 통신 패턴을 파악했습니다.

위협 인텔리전스 분석가는 이러한 공급망 공격 가능성을 조사할 책임이 있습니다. 공격자가 3CX 앱을 어떻게 침해했는지 파악하고, 잠재적인 위협 행위자를 식별하고, 사건의 전반적인 규모를 평가하는 것이 목표입니다.

# 문제 파일
msi 확장자의 윈도우 설치 프로그램이 하나 제공된다. 당황하지 말고 해시값을 확인한 후 VirustTotal에 검색해보자.

파일명: ``3CXDesktopApp-18.12.416.msi``

Hash (MD5): 0EEB1C0133EB4D571178B2D9D14CE3E9

# 개념 정리
공급망 공격 (Supply Chain Attack): 공격자가 소프트웨어, 하드웨어 또는 서비스의 공급망에 침투하여 악성 코드를 삽입하거나 시스템을 손상시키는 사이버 공격 유형. (ex. 개발사 네트워크에 침투하여 소스 코드에 악성 코드 삽입, 배포를 위한 서버에 접근해서 파일 변경 등)

3CX: 사용자에게 채팅, 화상 통화, 음성 통화 등 다양한 커뮤니케이션 기능을 제공하는 기업용 소프트웨어

3CX Supply chain attack:  2023년 3월 말 소프트웨어 공급망 침해 사고로 3CX 웹사이트에서 트로이 목마 악성코드가 유포됨

# Questions

## Q1
Understanding the scope of the attack and identifying which versions exhibit malicious behavior is crucial for making informed decisions if these compromised versions are present in the organization. How many versions of 3CX running on Windows have been flagged as malware?

공격 범위를 파악하고 어떤 버전이 악성 행위를 보이는지 파악하는 것은 조직 내에 이러한 감염된 버전이 존재하는 경우 정보에 기반한 의사 결정을 내리는 데 매우 중요합니다. Windows에서 실행되는 3CX 버전 중 몇 개가 맬웨어로 분류되었습니까?

### Answer
2

### 분석
시나리오와 VirusTotal에서 해당 악성코드의 정보를 획득한 뒤 관련해서 구글링을 진행하면 어떤 버전에서 취약점이 발견됐는지 확인할 수 있다.

![SCX_Supply_Chain_Q1_1.png](./IMG/SCX_Supply_Chain_Q1_1.png)

![SCX_Supply_Chain_Q1_2.png](./IMG/SCX_Supply_Chain_Q1_2.png)

취약점이 발견된 버전: Windows (versions 18.12.407 and 18.12.416) 

## Q2
Determining the age of the malware can help assess the extent of the compromise and track the evolution of malware families and variants. What's the UTC creation time of the .msi malware?

악성코드의 생성 시기를 확인하면 침해 정도를 평가하고 악성코드 계열 및 변종의 진화 과정을 추적하는 데 도움이 될 수 있습니다. .msi 악성코드의 UTC 생성 시간은 몇 시인가요?

### Answer
2023-03-13 06:33

### 분석
악성코드 생성시간: 2023-03-13 06:33:26 UTC

![SCX_Supply_Chain_Q2_1.png](./IMG/SCX_Supply_Chain_Q2_1.png)

## Q3
Executable files (.exe) are frequently used as primary or secondary malware payloads, while dynamic link libraries (.dll) often load malicious code or enhance malware functionality. Analyzing files deposited by the Microsoft Software Installer (.msi) is crucial for identifying malicious files and investigating their full potential. Which malicious DLLs were dropped by the .msi file?

실행 파일(.exe)은 1차 또는 2차 맬웨어 페이로드로 자주 사용되는 반면, 동적 연결 라이브러리(.dll)는 악성 코드를 로드하거나 맬웨어 기능을 강화하는 경우가 많습니다. Microsoft 소프트웨어 설치 관리자(.msi)에서 생성된 파일을 분석하는 것은 악성 파일을 식별하고 그 잠재력을 최대한 조사하는 데 매우 중요합니다. .msi 파일에서 어떤 악성 DLL이 드롭되었습니까?

### Answer
ffmpeg.dll,d3dcompiler_47.dll

### 분석
msi 파일에서 드롭된 악성 dll은 ffmpeg.dll과 d3dcompiler.dll이 있다.

![SCX_Supply_Chain_Q3_1.png](./IMG/SCX_Supply_Chain_Q3_1.png)

## Q4
Recognizing the persistence techniques used in this incident is essential for current mitigation strategies and future defense improvements. What is the MITRE Technique ID employed by the .msi files to load the malicious DLL?

이 사건에 사용된 지속성 기법을 파악하는 것은 현재의 완화 전략과 향후 방어력 향상에 필수적입니다. .msi 파일이 악성 DLL을 로드하는 데 사용하는 MITRE 기법 ID는 무엇입니까?

### Answer
T1574

### 분석
악성코드는 악성 DLL을 로드할 때 DLL-Side Loading 기법을 사용한다.

![SCX_Supply_Chain_Q4_1.png](./IMG/SCX_Supply_Chain_Q4_1.png)
![SCX_Supply_Chain_Q4_2.png](./IMG/SCX_Supply_Chain_Q4_2.png)

DLL-Side Loading 기법은 정상적인 응용 프로그램과 악성 DLL을 같은 경로에 저장하여 응용 프로그램이 실행 될 때 악성 DLL이 함께 동작하도록 하는 기법이다. 따라서 악성 DLL은 정상 프로그램이 참조하는 다른 경로에 위치한 정상 DLL 파일명과 동일하게 변경하여 악성 DLL이 먼저 실행 되도록 한다. (DLL을 로드하는 순서, 검색 순서를 악용하는 기법이다.)

링크: https://attack.mitre.org/techniques/T1574/001/

## Q5
Recognizing the malware type (threat category) is essential to your investigation, as it can offer valuable insight into the possible malicious actions you'll be examining. What is the threat category of the two malicious DLLs?

악성코드 유형(위협 범주)을 파악하는 것은 조사에 필수적입니다. 조사 대상 악성 행위에 대한 귀중한 통찰력을 제공할 수 있기 때문입니다. 두 악성 DLL의 위협 범주는 무엇입니까?

### Answer
trojan

### 분석
VirusTotal에서 카테고리를 확인할 수 있다.

![SCX_Supply_Chain_Q5_1.png](./IMG/SCX_Supply_Chain_Q5_1.png)
![SCX_Supply_Chain_Q5_2.png](./IMG/SCX_Supply_Chain_Q5_2.png)

## Q6
As a threat intelligence analyst conducting dynamic analysis, it's vital to understand how malware can evade detection in virtualized environments or analysis systems. This knowledge will help you effectively mitigate or address these evasive tactics. What is the MITRE ID for the virtualization/sandbox evasion techniques used by the two malicious DLLs?

동적 분석을 수행하는 위협 인텔리전스 분석가로서, 가상화된 환경이나 분석 시스템에서 악성코드가 탐지를 회피하는 방식을 이해하는 것은 매우 중요합니다. 이러한 지식은 이러한 탐지 회피 전략을 효과적으로 완화하거나 해결하는 데 도움이 될 것입니다. 두 악성 DLL에서 사용하는 가상화/샌드박스 탐지 회피 기법의 MITRE ID는 무엇입니까?

### Answer
T1497

### 분석
VirusTotal에서 가상화/샌드박스 탐지 회피 기법의 Mitre Att&k ID를 확인할 수 있다.

![SCX_Supply_Chain_Q6_1.png](./IMG/SCX_Supply_Chain_Q6_1.png)

## Q7
When conducting malware analysis and reverse engineering, understanding anti-analysis techniques is vital to avoid wasting time. Which hypervisor is targeted by the anti-analysis techniques in the ffmpeg.dll file?

맬웨어 분석 및 리버스 엔지니어링을 수행할 때 시간 낭비를 막기 위해 분석 방지 기술을 이해하는 것이 매우 중요합니다. ffmpeg.dll 파일의 분석 방지 기술은 어떤 하이퍼바이저를 대상으로 합니까?

### Answer
VMWare

### 분석
VirusTotal에서 ffmpeg.dll의 별도 분석 결과를 확인할 수 있다.

![SCX_Supply_Chain_Q7_1.png](./IMG/SCX_Supply_Chain_Q7_1.png)

확인해보면 VMWare를 탐지하고 우회하는 것으로 확인됐다.

![SCX_Supply_Chain_Q7_2.png](./IMG/SCX_Supply_Chain_Q7_2.png)

## Q8
Identifying the cryptographic method used in malware is crucial for understanding the techniques employed to bypass defense mechanisms and execute its functions fully. What encryption algorithm is used by the ffmpeg.dll file?

악성코드에 사용되는 암호화 방식을 파악하는 것은 방어 메커니즘을 우회하고 기능을 완벽하게 실행하는 데 사용되는 기법을 이해하는 데 매우 중요합니다. ffmpeg.dll 파일은 어떤 암호화 알고리즘을 사용합니까?

### Answer
RC4

### 분석
VirusTotal에서 암호화 알고리즘을 확인할 수 있다.

![SCX_Supply_Chain_Q8_1.png](./IMG/SCX_Supply_Chain_Q8_1.png)

## Q9
As an analyst, you've recognized some TTPs involved in the incident, but identifying the APT group responsible will help you search for their usual TTPs and uncover other potential malicious activities. Which group is responsible for this attack?

분석가로서, 당신은 이 사건에 연루된 몇몇 TTP를 파악했지만, APT 그룹을 식별하면 그들의 일반적인 TTP를 검색하고 다른 잠재적인 악성 활동을 발견하는 데 도움이 될 것입니다. 이 공격의 배후는 누구일까요?

### Answer
Lazarus

### 분석
북한의 라자루스 그룹

![SCX_Supply_Chain_Q9_1.png](./IMG/SCX_Supply_Chain_Q9_1.png)
![SCX_Supply_Chain_Q9_2.png](./IMG/SCX_Supply_Chain_Q9_2.png)


# 마무리
VirusTotal에는 생각보다 볼 정보가 많다.

참고한 보고서 리스트
- https://asec.ahnlab.com/ko/51915/
- https://www.fortinet.com/blog/threat-research/3cx-desktop-app-compromised
- https://www.trendmicro.com/en_us/research/23/c/information-on-attacks-involving-3cx-desktop-app.html