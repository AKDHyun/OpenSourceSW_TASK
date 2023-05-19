# OpenSourceSW TASK ![AKDH](https://github.com/AKDHyun/OpenSourceSW_TASK/assets/132863580/096c81f4-14fd-45bd-84b7-7304e5596349)
###### Chosun Univ. Computer Engineering. 20233178 고도현 [iNT]

---

# Linux Command ![LINUX](https://github.com/AKDHyun/OpenSourceSW_TASK/assets/132863580/238dd7ec-55f5-457f-923d-3288c8266ebc)

## top
### 리눅스에서 실행 중인 프로세스들의 실시간 정보를 모니터링하는 명령어
CPU 사용량, 메모리 사용량, PID 등의 시스템 리소스 사용 상황과 프로세스들의 동작을 실시간으로 확인할 수 있다.

###### 기본 형식
```css
top [옵션]
```
'top'명령어를 사용하면 다음과 같은 정보를 확인할 수 있다
```yaml
top - 02:48:05 up 0 min,  0 users,  load average: 0.07, 0.02, 0.00
Tasks:   6 total,   1 running,   5 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.0 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7889.9 total,   7394.8 free,    276.8 used,    218.4 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   7389.0 avail Mem
Change delay from 3.0 to
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    1 root      20   0    2324   1508   1404 S   0.0   0.0   0:00.00 init(Ubuntu)
    4 root      20   0    2748    356     68 S   0.0   0.0   0:00.00 init
    8 root      20   0    2328    112      0 S   0.0   0.0   0:00.00 SessionLeader
    9 root      20   0    2344    116      0 S   0.0   0.0   0:00.00 Relay(10)
   10 root      20   0    7492   5096   3388 S   0.0   0.1   0:00.06 bash
   58 root      20   0    9208   3652   3064 R   0.0   0.0   0:00.00 top
```
+ PID (Process ID) : 프로세스의 고유한 식별자인 프로세스 ID
+ USER (Username) : 프로세스를 실행한 사용자 계정
+ PR (Priority) : 프로세스의 우선 순위, 값이 작을수록 더 높은 우선 순위를 가짐
+ NI (Nice Value) : 프로세스의 Nice 값, 즉 프로세스의 우선 순위를 조정하는 값, 높은 값일수록 낮은 우선 순위를 의미
+ VIRT (Virtual Memory) : 프로세스가 사용하는 가상 메모리의 크기, 단위는 킬로바이트(kb)
+ RES (Resident Memory) : 프로세스가 실제로 메모리에 사용 중인 메모리의 크기, 단위는 킬로바이트(kb)
+ SHR (Shared Memory) : 프로세스가 공유하는 메모리의 크기, 단위는 킬로바이트(kb)
+ S (Status) : 프로세스의 상태, R (Running, 실행 중) / S (Sleeping, 대기 중)
+ %CPU (CPU Usage) : 프로세스가 사용하는 CPU의 사용량을 백분율로 나타냄
+ %MEM (Memory Usage) : 프로세스가 사용하는 메모리의 사용량을 백분율로 나타냄
+ TIME+ (CPU Time) : 프로세스가 실행된 총 CPU 시간
+ COMMAND : 프로세스를 시작한 명령어 또는 프로세스의 실행 파일을 나타냄

'top'에서는 다양한 키를 사용하여 정렬, 필터링, 프로세스 종료 등의 작업을 수행할 수 있다

###### 주요옵션
+ '-d <초>' : 갱신 간격 지정, 지정된 시간(초)마다 화면 갱신
+ '-n <횟수>' : 표시할 반복 횟수를 지정, 지정된 횟수만큼 정보를 갱신한 후 top 종료
+ '-p <PID>' : 특정 PID의 프로세스만 표시, 여러 개의 PID를 쉼표로 구분하여 지정 가능
+ '-u <사용자명>' : 특정 사용자의 프로세스만 표시
+ '-s <필드>' : 정렬할 필드를 지정, ex) 'top -s %CPU'는 CPU 사용량에 따라 프로세스를 정렬
+ '-b' : 배치 모드로 실행, 화면을 갱신하지 않고 프로세스 정보를 한 번만 출력하고 top 종료


  
## ps
### 현재 실행 중인 프로세스의 정보를 표시하는 명령어
시스템에서 실행중인 프로세스의 목록을 보거나 원하는 정보를 선택적으로 표시할 수 있다.

###### 기본 형식
```css
ps [옵션]
```
'ps'명령어를 사용하면 다음과 같은 정보를 확인할 수 있다
```
  PID TTY          TIME CMD
   10 pts/0    00:00:00 bash
   76 pts/0    00:00:00 top
 2636 pts/0    00:00:00 ps
```
+ PID : 프로세스의 고유한 식별자인 프로세스 ID
+ TTY : 프로세스가 연결된 터미널 장치, 해당 프로세스가 터미널과 직접 상호작용하는 경우에만 값을 가짐
+ TIME : 프로세스가 실행된 CPU시간, "시:분:초" 형식으로 표시
+ CMD : 프로세스를 시작한 명령어 또는 프로세스의 실행 파일을 나타냄

###### 주요옵션
+ '-e' : 시스템에서 실행 중인 모든 프로세스 표시
+ '-f' : 자세한 형식으로 프로세스 정보 표시
+ '-l' : 긴 형식으로 프로세스 정보 표시
+ '-u <사용자명>' : 특정 사용자의 프로세스만 표시
+ '-p <PID>' : 특정 PID의 프로세스만 표시


  
## jobs
### 현재 세션에서 실행 중인 백그라운드 작업을 나열하는 명령어
리눅스 쉘에서 백그라운드에서 실행 중인 작업들을 추적하고 관리할 수 있도록 도와준다.

###### 기본 형식
```bash
jobs
```
'jobs'명령어를 사용하면 다음과 같은 정보를 확인할 수 있다
```
[1]   Running                 command1 &
[2]-  Stopped                 command2
[3]+  Running                 command3 &
```
+ 작업 번호 : 백그라운드에서 실행 중인 작업들을 일련번호로 식별
+ +/- : 마지막으로 실행된 작업과 이전 작업을 구분
+ 상태 : 작업의 현재 상태를 나타냄 (Running/Stopped)
+ 명령어 : 실행 중인 작업에 해당하는 명령어나 스크립트 이름 표시

###### 옵션
+ '-l' : 작업 목록에 상세 정보를 포함하여 표시
+ '-n' : 작업 목록에서 작업 번호를 표시하지 않음



## kill
### 리눅스에서 프로세스를 종료하는 명령어
특정 프로세스에 시그널을 보내어 프로세스를 종료하거나 동작을 변경할 수 있다.

###### 기본 형식
```bash
kill [옵션] <PID 또는 작업번호>
```
여기서 프로세스 ID는 'ps'명령어를 사용하여 확인할 수 있고, 작업번호는 'jobs'명령어를 통해 확인할 수 있다
  
 ###### 주요옵선
+ '-l' 또는 '--list' : 사용 가능한 시그널 목록 표시
+ '-s <시그널>' 또는 '--signal=<시그널>' : 특정 시그널 지정, 기본적으로 SIGTERM 시그널(15번)이 사용되며 프로세스에 종료 신호를 보냄
+ '-<시그널>' : -s 옵션과 동일한 역할, 약식으로 사용
  
  
  
  
  
  
![ENDLINE](https://github.com/AKDHyun/OpenSourceSW_TASK/assets/132863580/6e4b1c99-2c93-46d2-ba04-50da2e288130)
