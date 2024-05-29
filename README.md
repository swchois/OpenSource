# OpenSource
오픈 소스 수업시간 실습 내용 정리


과제 내용 
---
## 리눅스 명령어 정리

### 1. Top
   - 정의
     
   **top 명령어는 리눅스 계열 서버의 OS 상태를 확인할 수 있는 CLI 어플리케이션이다.**
   top 명령어를 통해 서버의 CPU 사용량, 메모리 사용량 등을 확인할 수 있으며, 서버에서
   구동 중인 모든 어플리케이션들을 CPU 사용률이나 메모리 사용률이 많은 순서대로 나열하여 모니터링이 가능한 명령어이다.
  ![image](https://github.com/swchois/OpenSource/assets/130259157/4f03607b-b31e-4861-a9f7-92c7cf2de384)

- top 명령어 사용법

  단순 top 명령어를 실행하는 것만으로 사용이 가능하다.
  
  리눅스 서버에서 top 명령어를 입력하면 다음과 같은 결과를 얻을 수 있다.

![image](https://github.com/swchois/OpenSource/assets/130259157/8b863177-5bfc-4d82-93ad-5027e223a306)

   현재 시간을 표시해주고 있으며, 서버가 구동된지 14분 된 것을 알 수 있으며,

   현재 0명이 서버에 붙어있으며, load avg 값을 볼 수 있다.

![image](https://github.com/swchois/OpenSource/assets/130259157/7d7ac616-bed6-4360-910c-5f5700e6d822)
   두 번째 줄은 총 2개의 프로세스가 수행 중이며, 1개의 프로세스가 실행 중인 것을 알 수 있다.   
![image](https://github.com/swchois/OpenSource/assets/130259157/8fd779b7-86df-4a0b-ac77-e84c4e0ab9bc)
   3번째 줄은 cpu 사용량을 볼 수 있다.

   us: 사용자 레벨의 CPU 사용 비중
   
   sy: 시스템 레벨의 CPU 사용 비중
   
   ni: 우선순위가 낮은 프로세스의 CPU 비중
   
   id: 유휴 상태의 CPU사용 비중
   
   wa: I/O 를 대기 중인 cpu 사용률
   
   hi: interrupt handler에서 사용 중인 cpu 사용률, 빠르게 수행을 마쳐야 하는 작업
   
   si: hi에서 오래 걸리는 작업 때문에 미뤄놓은 작업
   
   st: 하이퍼바이저가 다른 가상 프로세서를 서비스하는 동안 가상 CPU가 실제 CPU를 기다리는 시간

   ![image](https://github.com/swchois/OpenSource/assets/130259157/fa025478-71fc-4d86-a9f6-1ad31a59d71a)
   4번째 줄은 메모리 관련 정보이다.


 --- 
### 2. ps

- 정의

  ps 명령어는 Process State의 약자로 **현재로 실행 중인 프로세스와 상태**를 출력하는 명령어이다.
  - 옵션
  
  |옵션|설명
  |:---:|:---:|
  |-e| 실행중인 모든 프로세스의 정보를 출력한다.|
  |-f | 프로세스에 대한 자세한 정보를 출력한다 (PPID 확인 가능)|
  |-u[사용자이름]| 특정 사용자에 대한 모든 프로세스의 정보를 출력|
  |-p pid | pid로 지정한 프로세스의 정보를 출력|
  |u| 프로세스 소유자의 이름, CPU 사용량, 메모리 사용령 등 상세 정보를 출력|
  |a| 터미널에서 실행한 프로세스의 정보를 출력|
  |x| 실행 중인 모든 프로세스의 정보를 출력|


  ![image](https://github.com/swchois/OpenSource/assets/130259157/b9f39c3a-3320-4f34-a6c8-a3cd55d705b7)

  ps 명령어 사용 사진이다.

  ![image](https://github.com/swchois/OpenSource/assets/130259157/49209b3e-9a99-47c0-b98e-7f9caa033759)

  ps -f 사진이다.

  ![image](https://github.com/swchois/OpenSource/assets/130259157/6c7e6a83-0523-47e4-881d-a330a9d18589)

ps -uroot 사진이다.

---
### 3. jobs

- 정의

  **jobs는 셸에서 실행한 프로세스 목록을 확인**하는 명령어이다.

  특히 bg, fg 명령어와 함께 셸에서 실행한 프로세스들을 백그라운드나 포그라운드로 전환하는 용도로 많이 사용한다.

  ![image](https://github.com/swchois/OpenSource/assets/130259157/b32ff1a3-3938-4798-bbc7-0f8c268c2160)

  현재 실행되는 작업이 없어서 아무것도 출력이 되지를 않는다.

![image](https://github.com/swchois/OpenSource/assets/130259157/fd22ba54-369b-4296-9eea-b39e4640abdd)

sleep을 백그라운드에서 실행하고 jobs 명령오로 프로세스 목록을 확인해보았다.

대괄호 안의 숫자는 job ID가 된다. 

그 다음에 있는 +는 bg 나 fg 명령 실행시 기본 인자로 사용된다는 의미이며

-는 +로 표시된 프로세스가 종료시 기본 값으로 사용될 프로세스를 의미한다.

Running: 두 번째 열은 프로세스의 상태를 나타낸다. 현재는 Running 으로 실행중인 상태를 의미한다.

뒤에는 프로세스를 실행한 명령어를 나타낸다.

jobs 에 인자를 지정하면 특정 프로세스만 확인할 수 있다.

![image](https://github.com/swchois/OpenSource/assets/130259157/cefc8e3f-6112-423a-ad46-8814af473243)

- 옵션
  
|9옵션|설명
|:---:|:---:|
|-l| 프로세스 ID와 함께 job 목록을 출력한다.|
|-n| 마지막으로 알림 이후 변경된 job만 출력한다. |
|-p| job의 프로세스 ID만 출력한다.|
|-r| 실행 중인 job 출력한다.|
|-s| 중지된 잡만 출력한다.|

---
### 4. kill

- 정의

  kill 명령어는 프로세스를 강제로 종료시키는 명령어로 오해를 사기 좋으나 **실제로는 프로세스에 시그널을 보내는 명령어**이다.

![image](https://github.com/swchois/OpenSource/assets/130259157/ee8e2b0f-dd6a-4b2a-a4a1-859f1b139dae)

kill -l 을 통해서 시그널의 숫자와 이름이 출력된다.

시그널을 보낼때는 **kill -(보낼 시그널) PID** 이런식으로 사용한다.

- 옵션

|옵션|설명|
|:---:|:---:|
|-9| 프로세스 ID를 직접 지정하여 종료시 사용 된다|
|-l| 신호(Signal)로 사용할 수 있는 신호(Signal) 이름들을 보여준다 |

- 사용가능 신호

|번호|신호이름|신호|의미|
|:---:|:---:|:---:|:---:|
|1|SIGHUP|HUP|hangup, 로그아웃등의 접속이 끊을 때 발생하는 신호(Signal)로 특정 실행 중인 프로그램이 사용하는 설정 파일을 변경시키고 변화된 내용을 적용할때 사용됩니다.|
|2|SIGINT|INT|현재 작동중인 프로그램의 동작을 멈출때 사용되며, 일반적인 값은 <CTRL>+<c> 입니다.|
|9|SIGKILL|KILL|프로그램을 무조건 종료할 경우 사용됩니다.|
|11|SIGSEGV|SEGV|잘못된 메모리 관리시 생기는 신호(Signal) 입니다.|
|15|SIGTERM|INT|실행중인 프로그램을 정상적인 종료방법으로 프로그램을 종료하는 신호(Signal)로 kill 명령에서 신호(Signal)를 지정하지 않으면 이 신호(Signal)를 사용하여 프로그램을 종료합니다.|
|18|SIGCONT	|CONT|중지 되어 있는 프로그램을 재실행 하는데 사용되는 신호(Signal) 입니다.|
|20|SIGTSTP|TSTP|터미널에서 중지되어 있는 신호(Signal) 입니다.|



---
