## 리눅스 명령어 top, ps, jobs, kill 조사하기

**1. top 명령어**
현재 OS의 상태를 알려주는 명령어로 메모리 사용량, CPU 사용량을 알려준다.
**top 명령어를 실행시키면 상단에 프로세스가 OS에서 리소스를 차지하는 비율을 알려주며 시간, 유저, 로드 에버리지(Load Average), 테스크(Tasks), CPU, 메모리(memory)가 나타난다.**
옵션없이 실행시키면 3초 간격으로 화면을 갱신하며 정보를 제공한다.

**top 명령어의 상세한 내용은 PID, USER, PR&NI, VIRT, RES, SHR, %MEM, S, TIME+, COMMAND가 있다.**

-PID
프로세스 아이디를 나타낸다. 프로세스를 구분하기 위하여 겹쳐지지 않는 고유한 값이다.
-USER
해당 프로세스를 실행한 USER NAME 또는 효과를 받는 USER NAME이다.
-PR&NI
PR은 커널에 의해서 스케줄링 되는 우선순위이다.
NI는 PR에 영항을 주는 nice라는 값을 의미한다.
-VIRT
프로세스가 소비하고 있는 총 메모리이다.
-RES
RAM에서 사용중인 메모리의 크기를 나타낸다.
-SHR
다른 프로세스와의 공유메모리를 나타낸다.
-%MEM
RAM에서 RES가 차지하는 비율을 나타낸다.
-S
프로세스의 현재 상태를 나타낸다.
-TIME+
프로세스가 사용한 토탈 CPU 시간이다.
-COMMAND
해당 프로세스를 실행한 커맨드를 나타낸다.

**top 명령어 옵션**
-shift + p : CPU 사용률 내림차순을 나타낸다.
-shit + m : 메모리 사용률 내림차순을 나타낸다.
-shift + t : 프로세스가 돌아가고 있는 시간 순을 나타낸다.
-k : kill명령어이다. k 입력 후 PID 번호 작성한다.
-f : sort field 선택 화면이며 q를 누르면 RES 순으로 정렬한다.
-a : 메모리 사용량에 따라 정렬한다.
-b : Batch 모드로 작동한다.
-1 : CPU Core별로 사용량 보여준다.

**2. ps 명령어**
현재 OS에서 실행중인 프로세스의 목록과 상태를 보여주는 명령어이다.
**ps 명령어를 실행하면 PID, TTY, TIME, CMD가 나타난다**

-PID
프로세스 아이디를 나타낸다. 프로세스를 구분하기 위하여 겹쳐지지 않는 고유한 값이다.
-TTY
터미널 번호를 나타낸다.
-TIME
해당 프로세스가 사용한 CPU 시간의 양을 나타낸다.
-CMD
프로세스가 실행중인 명령어가 무엇인지 나타낸다.

**ps 명령어 옵션**
-e : 실행중인 모든 프로세스의 정보를 출력한다.
-f : 프로세스에 대한 자세한 정보를 출력한다(UID, PID, PPID, C - CPU, STIME, TTY, TIME, CMD). 
-u [USER NAME] : 특정 사용자에 대한 모든 프로세스 정보를 출력한다.
-p pid : pid로 지정한 프로세스의 정보를 출력한다.
-u : 프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세한 정보를 출력한다.
-a 터미널에서 실행한 프로세스의 정보를 출력하며 STAT(프로세스의 상태)을 나타낸다.
-x : 실행중인 모든 프로세스의 정보를 출력한다.

**3. jobs 명령어**
작업의 상태를 표시하는 명령어이며, 현재 쉘 세션에서 실행시킨 백그라운드 프로세스가 출력된다.
각 작업에는 번호가 붙어있어 kill 명령어 뒤에 '%번호'로 사용 가능하다.
**josbs 명령어로 나타나는 작업의 상태값들은 RUNNING, DONE, DONE(CODE), STOPPED, STOPPED(SIGTSTP), STOPPED(SIGSTOP), STOPPED(SIGTTIN), STOPPED(SIGTTOU)이 있다.**

- RUNNING
작업이 계속 진행중이다.
- DONE
작업이 완료되어 0을 반환한다.
- DONE(CODE)
작업이 종료되었으며 0이 아닌 코드를 반환한다.
- STOPPED
작업이 일시 중단되었다.
- STOPPED(SIGTSTP)
SIGTSTP 시그널이 작업을 일시 중단한다.
- STOPPED(SIGSTOP)
SIGSTOP 시그널이 작업을 일시 중단한다.
- STOPPED(SIGTTIN)
SIGTTIN 시그널이 작업을 일시 중단한다.
- STOPEED(SIGTTOU)
SIGTTOU 시그널이 작업을 일시 중단한다.

**jobs 명령어 옵션**
-l : 프로세스 그룹 ID를 state 필드 앞에 출력한다.
-n : 프로세스 그룹 중에 대표 프로세스 ID를 출력한다.
-p : 각 프로세스 ID에 대해 한 행씩 출력한다.
command : 지정한 명령어를 실행한다.

**4. kill 명령어**
프로세스를 종료하는 명령어이며, 프로세스에 시그널을 보내 원하는 작업을 실행시키도록 한다.
**프로세스를 종료시키기 위해서는 해당 프로세스의 PID를 알아야 한다.**

**kill 명령어 옵션**

-kil[PID] : 죽이려는 프로세스의 pid를 kill 명령어의 파라미터로 넘겨 실행을 종료시킨다.
-l : signal의 종류를 출력한다.
-kill[OPTION] PID : 프로세스에 시그널을 보낸다.

**kill 명령어의 주요 시그널**

-SIGHUP : 세션이 종료될 때 시스템이 내리는 시그널이다.
-SIGINT : Ctrl + C, 종료 요청 시그널이다.
-SIGKILL : 강제 종료 시그널이다.
-SIGSEGV : 기본값, 종료 요청 시그널이다.
-SIGTSTP : Ctrl+ Z, 일시 중지 요청 시그널이다.

**kill 명령어 프로세스 종료**

-kill -9 PID
-kill -SIGKILL PID

## Vim 에디터에서 매크로 사용방법에 대하여 조사하기

**매크로 사용법(q, @)**
+ vim의 명령모드에서 q를 누른 후 매크로의 이름으로 사용할 알파벳을 입력한다.(ex: qa qd qe)
+ 이름 알파벳이 입력되면 매크로를 기록을 시작하며 하단에 --recording--이 표시된다.
+ 사용하고 싶은 매크로의 내용을 입력한다.
+ 기록을 끝내고 싶다면  다시 q를 입력한다.
+ 기록한 매크로를 사용하고 싶으면 @[NAME]을 입력하면 매크로가 재생된다.(ex: @a @d @e)
+ [숫자]@[NAME]을 실행시키면 입력한 숫자만큼 매크로가 실행된다.
