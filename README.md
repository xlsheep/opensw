<div alighn=center>

<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=200&section=header&text=OpenSW_homework&fontSize=80" />

리눅스에서 `top`, `ps`, `jobs`, `kill` 명령어들을 소개하겠습니다. 

### 목차
- top
  - 예시
  - 추가옵션
- ps
  - 예시
  - 추가옵션
- jobs
  - 예시
- kill
  - 예시
  - 추가옵션

이 명령어들은 시스템에서 실행 중인 프로세스를 확인하고 관리하는 데 도움을 줍니다. 

### top❓

`top` 명령어는 시스템에서 실행 중인 프로세스들을 실시간으로 보여주는 명령어입니다. 

CPU 사용량이나 메모리 사용량 같은 시스템 자원의 사용 현황을 확인할 수 있습니다.

**예시:**

```
$ top
```

실행 결과는 다음과 같은 화면이 나타납니다. 
(출력 결과는 시스템에 따라 상이합니다.)

```
Processes: 581 total, 4 running, 577 sleeping, 2849 threads                         20:16:00
Load Avg: 3.48, 3.45, 2.88  CPU usage: 17.94% user, 7.60% sys, 74.44% idle
SharedLibs: 846M resident, 160M data, 69M linkedit.
MemRegions: 320038 total, 5564M resident, 446M private, 3028M shared.
PhysMem: 17G used (1888M wired, 936M compressor), 108M unused.
VM: 245T vsize, 4892M framework vsize, 0(0) swapins, 0(0) swapouts.
Networks: packets: 527097/573M in, 223613/51M out.
Disks: 389284/9147M read, 384538/8202M written.

PID   COMMAND      %CPU TIME     #TH    #WQ  #PORT MEM    PURG  CMPRS  PGRP PPID STATE
1072  Google Chrom 67.0 13:08.57 21     5    357+  652M+  250M  24M    1066 1066 sleeping
3317  Google Chrom 58.0 05:02.69 22/1   1    223   287M-  0B    0B     1066 1066 running
363   WindowServer 50.8 45:15.99 20     5    2622+ 689M-  236M+ 43M    363  1    sleeping
2057  iTerm2       40.7 02:38.98 8      5    405   302M-  230M+ 28M    2057 1    sleeping
0     kernel_task  21.6 16:10.66 566/11 0    0     9184K  0B    0B     0    0    running
394   coreaudiod   10.0 09:17.82 11     2    848   33M    0B    7648K  394  1    sleeping
...
```

#### 추가적인 옵션
| 옵션 | 의미 |
|------|------|
| `-n` | 지정한 숫자만큼 화면 출력을 갱신한 후 종료 |
| `-u` | 지정한 사용자의 프로세스를 모니터링 |
| `-b` | 출력 결과를 파일이나 다른 프로그램으로 전달 |
| `-d` | 화면 갱신 주기를 초 단위로 설정 |
| `-p` | 지정한 PID의 프로세스를 모니터링 | 


### ps❓

`ps` 명령어는 현재 실행 중인 프로세스의 목록을 보여줍니다. 
사용자는 이를 통해 특정 프로세스의 상태를 확인할 수 있습니다.

(설명하기전 System V 의 경우 -를 사용하고 BSD는 같은 경우는 -를 쓰지 않습니다.
저는 BSD기반의 맥이기에 BSD 경우를 설명하겠습니다.)

**예시:**

```
$ ps
```
실행 결과는 다음과 같은 화면이 나타납니다. 
(출력 결과는 시스템에 따라 상이합니다.)

```
  PID TTY          TIME CMD
 1131 ttys000    00:00:00 -zsh
 2048 ttys001    00:00:00 -zsh
...
```
#### 추가적인 옵션(BSD기반)
| 옵션 | 의미 |
|------|------|
| `a`  | 터미널과 연관된 프로세스 출력. 보통 `x` 옵션과 연계하여 모든 프로세스를 출력할 때 사용 |
| `e`  | 프로세스에 관련된 환경 변수 정보 출력 |
| `f`  | 프로세스간 상속관계를 트리형식으로 출력 |
| `l`  | 프로세스의 정보를 길게 보여줌 |
| `u`  | 프로세스의 소유자를 기준으로 출력 |
| `x`  | 터미널에 종속되지 않는 프로세스 출력 |
| `p`  | 지정한 프로세스 출력 |


### jobs❓

`jobs` 명령어는 현재 세션에서 백그라운드로 실행 중인 작업의 목록을 보여줍니다.

**예시:**

```
$ jobs
```

만약 사용자가 몇 가지 프로세스를 백그라운드로 실행시켰다면 다음과 같은 결과를 볼 수 있습니다.

+는 스택의 가장 위에 있다는 뜻입니다

-는 바로 그다음 밑에 있다는 뜻입니다
```
[1]-  Running                 ./script.sh &
[2]+  Stopped                 nano myFile.txt
```


### kill

`kill` 명령어는 특정 프로세스를 종료시키는 데 사용됩니다. 
이 때, 프로세스 ID(PID)를 사용하여 특정 프로세스를 지정할 수 있습니다.

**예시:**

```
$ kill 2048
```

이 명령어는 PID가 2048인 프로세스를 종료시킵니다.

#### 추가적인 옵션
| Option        | Meaning |
|---------------|---------|
| `-signal`, `-s signal` | Sends the specified signal |
| `-l`          | Outputs a list of available signals | 


---

<img src="https://img.shields.io/badge/리눅스 명령어 간단 요약-FCC624?style=flat&logo=Linux&logoColor=white"/>

| 명령어 | 설명 | 사용 예 |
|--------|------|---------|
| `top`  | 시스템에서 실행 중인 프로세스들을 실시간으로 보여줍니다. 
CPU 사용량이나 메모리 사용량 같은 시스템 자원의 사용 현황을 확인할 수 있습니다. | `$ top` |
| `ps`   | 현재 실행 중인 프로세스의 목록을 보여줍니다. 사용자는 이를 통해 특정 프로세스의 상태를 확인할 수 있습니다. | `$ ps` |
| `jobs` | 현재 세션에서 백그라운드로 실행 중인 작업의 목록을 보여줍니다. | `$ jobs` |
| `kill` | 특정 프로세스를 종료시키는 데 사용됩니다. 프로세스 ID(PID)를 사용하여 특정 프로세스를 지정할 수 있습니다. | `$ kill 2048` |



이 명령어들은 리눅스 시스템에서 프로세스를 모니터링하고 관리하는 데 필수적인 도구입니다. 

<img src="https://capsule-render.vercel.app/api?type=waving&color=BDBDC8&height=200&section=footer" />

</div>


