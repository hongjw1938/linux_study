## 리눅스 tutorial
### 0. 리눅스 환경 구축하기
- 아래의 내용은 생활코딩 강의를 바탕으로 정리한 것.
- <a href="https://opentutorials.org/course/2598">생활코딩 강좌</a>
- 리눅스를 직접 설치하는 것은 번거롭다. 따라서 웹 서비스를 이용해 즉각적으로 리눅스를 사용할 수 있도록 환경을 구축한다.
- 방법
    1. CodeOnWeb에서 실습환경을 구축한다. 좌측의 실행환경에서 Linux shell을 선택하면 linux사용환경이 구축된다.
    2. C9.io에서 linux환경을 구축한다.
    3. 가상머신을 이용한다.
### 1. 명령어(CLI환경 : command line interface, 명령어로 조작하는 환경)
- 명령어는 현재 디렉토리를 대상으로 하여 실행된다.
- 명령어(parameter를 이용해 해당 명령어의 실행 방식을 다룰 수 있다.)
    - ls : 현재 목록을 확인한다.(아래는 parameter)
        - -l : 현재 디렉토리의 파일 및 하위 디렉토리를 자세히 보여준다.
            - 제일 좌측의 d는 directory를 의미하며, -는 file을 의미한다.
            - 중간의 4096과 같은 숫자는 용량을 의미한다.
        - -a : .으로 시작하는 파일도 모두 보여준다.(.으로 시작하는 것은 숨김파일)
        - -S : file size에 따라 정렬한다.
    - pwd : 현재 위치를 확인한다.
    - mkdir directory_name : 지정한 name의 directory를 만든다.
    - touch 파일명 : 비어있는 해당 name의 file을 생성한다.
    - rm : 파일을 삭제한다.
    - cp : 파일을 복사한다.
    - mv : 파일을 이동시킨다., 파일 이름을 변경시킬 때도 이를 사용
    - cat file_name : 파일 이름을 출력
    - grep <정보> <파일명> : 특정 정보가 포함된 행을 찾는 명령
    - ps : 실행중인 process를 보여준다.
        - ps ax : 모든 프로세스를 볼 수 있다.(u까지 넣으면 자세하게 보여줌)
        - -o : 실행시 특정 칼럼만 출력시킬 수 있다.
    - head, tail : 앞의 뒷의 내용을 일부만 출력
    - history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head -10 : 내가 쳤던 명령어 history를 빈도수에 따라 정렬해서 보여줌
- 명령어 사용법을 확인하는 방법
    - --help를 특정 명령어 뒤에 지정한다.
        - ex) `ls --help` : ls명령어의 manual을 확인가능
    - man
        - `man ls` 와 같이 사용한다.
        - 새로운 페이지로 들어가서 확인한다.
        - 방향키를 이용해 이동할 수 있으며, 특정 내용을 찾고 싶은 경우 명령환경에서 `/내용`를 사용한다.
        - n키를 이용해 찾는 내용의 다음내용으로 이동 가능, shift+n을 통해 이전 검색 내용으로 이동 가능
        - q를 사용해 나올 수 있다.
    - man과 help의 차이 : man은 전용페이지로 이동해 상세한 메뉴얼을 보이며, help는 간략하다.
    - ex) `mkdir --help`
        - `Usage: mkdir [OPTION]... DIRECTORY...` : 사용법을 의미하며, option을 줄 수 있고 그 뒤에 DIRECTORY를 지정하는 것.
        - OPTION은 바로 아래의 arguments들을 지정가능
            - 해당 예로 -p를 OPTION으로 주면, 필요시 부모 디렉토리를 생성한다.
            - `mkdir -p dir1/dir2/dir3/dir4` : 부모디렉토리로 계속 생성
            - OPTION은 -p처럼 축약형 혹은 --parents와 같이 full로 지정가능
- 필요한 명령어를 검색하여 찾기
    - google 검색엔진에서 검색한다.
         - ex) create directory in linux와 같이 검색해보면 된다.
    - <a href="https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners">참조</a>
- sudo
    - sudo : super user do, 즉 super user가 하는 일이라는 것.
    - unix 계열의 운영체제는 다중 사용자 시스템이라는 특징을 가진다. 하나의 운영체제를 여럿이 사용해서 공동체가 형성된다.
    - 그래서, 파일의 권한을 지정하는 것이 중요하다.(permission)
    - 근데, 항상 슈퍼유저로써 권한을 가진 상태에서 명령을 실행하다 보면 매우 위험한 상황이 일어날 수 있다. 그래서 평시에는 일반유저로, 필요시에 sudo를 사용해 권한을 얻는것이다.
    - `apt-get install git` : 이를 실행해보면 permission이 denied된다. root유저가 아니기 때문
    - 이 때, `sudo apt-get install git`으로 하면 가능하다.
### 2. editor
- 파일 편집(nano editor)
    - `nano`를 입력하면 editor를 열 수 있다.
    - editor아래 쪽에는 ^G, ^O와 같이 있는데 ^는 ctrl을 의미한다.
    - 따라서, ctrl + O는 WriteOut이므로 누르면 fileName을 지정하라고 하는데 hello.html로 입력하고 enter를 누르면 `Wrote n lines`라고 나온다.
    - 그것은, 저장되었다는 것을 의미한다. ctrl+X를 누르고 나가서 ls로 확인가능
    - 다시 해당 파일을 수정하고 싶다면 `nano hello.html`로 하면 된다.
    - ctrl + k로 잘라내고 ctrl + u로 붙여넣을 수 있다.(capslock이 반드시 꺼져 있어야 한다. 켜있으면 shift도 눌러야함)
    - ctrl+shift(안눌러도 되는 경우도 있는 듯)+6으로 markset을 사용가능. markset을 이용해 block을 지정할 수 있고 그를 통해 특정 문구를 잘라내고 붙여넣을 수 있다.
    - ctrl+w로 검색할 수 있다.(c9환경에서는 ctrl+alt+shift를 누르고 명령을 수행하라.)
- vi editor
### 3. package manager
- package란 프로그램, app과 같은 것을 의미한다. package를 이용하여 컴퓨터의 다양한 처리를 한다.
- package manager는 app store와 같이 package를 다운로드받거나 관리할 수 있는 것이다.
- apt(패키지 매니저)
    - sudo apt-get update : apt라는 manager를 이용하여 다운받을 수 있는 목록을 최신상태로 update한다.
    - sudo apt-cache search name : name에 해당하는 다운로더블한 패키지를 확인 가능
        - top : window에 있는 작업관리자와 같은 것이다. 이를 좀 더 graphical하게 볼 수 있도록 htop설치
    - sudo apt-get : 설명서 나옴
    - sudo apt-get install htop : htop설치가능
    - sudo apt-get upgrade : 모든 package를 다 upgrade(특정 패키지만 업그레이드 하고 싶은 경우 이름을 주면 된다.)
    - sudo apt-get remove name : 특정 package 삭제
    - sudo apt-get dist-upgrade : 의존성 검사 후 업그레이드
    - sudo apt-get --reinstall install <package name> : 패키지 재설치
    - sudo apt-get --purge remove <package name> : 설정파일까지 모두 지움
    - sudo apt-get source <package name> : 패키지 소스코드 다운로드
    - sudo apt-get build-dep <package name> : 소스코드를 의존성 있게 빌드
    - sudo apt-cache show <package name> : 패키지 정보 보기
### 4. File download
- wget url : url을 통해서 파일을 다운로드받을 수 있다.
    - -O를 통해서 직접 이름을 지정할 수 있다.
    - wget --help를 이용해 manual을 확인하자
- git을 이용한 github url의 source를 받기
    - git clone url을 이용해 다운로드 받을 수 있다.
### 5. GUI vs CLI
- CLI를 사용하는 이유
    - GUI는 사용하기 편리하지만 computer의 resource를 매우 많이 잡아먹는다.
    - GUI는 순차적으로 진행되는 일을 자동화하기 어렵다.
- 순차적 실행?
    - mkdir why; cd why : why디렉토리를 만들고 거기로 이동한다.
    - 따라서, 이 명령어를 통해 거둘 수 있는 효과는 앞으로 필요한 process를 자동적으로 수행하고 최종 결과를 사용자에게 가져다준다는 것
    - 만약 매우 복잡하고 시간이 오래 걸릴 수 있는 명령어가 있는 경우 순차적으로 실행후 결과만 볼 수 있다.
- pipeline
    - 하나의 명령(프로그램, 프로세스)의 출력을 다른 명령(프로그램, 프로세스)의 입력으로 준다.
    - 예를 들어, grep을 이용해 특정 정보를 가진 행만을 화면에 보여주고 싶은 경우
    - `ls --help | grep sort` : ls의 manual 결과를 가지고 해당 내용에서 sort라는 정보를 가진 행만 출력해준다.
### 6. IO Redirection
- I : input, O : output 으로 입출력을 의미하며, redirection은 방향을 바꾼다는 의미다.
    - input과 output은 standard한 방식이 존재한다.
    - 표준 입력 및 출력이며, error의 경우에도 존재한다.
- process는 기본적으로 입력과 출력을 갖는다.
    - 예를 들어, `ls -al` 이라면 -al은 입력값이다.(command line arguments)
    - 또한 해당 결과를 화면에 보여주는데, 이것이 standard output
    - 이 standard output의 방향을 바꾸어서 파일로 redirection이 가능하다.
- `>` : 이 기호를 통해서 출력할 결과를 특정 파일에 저장할 수 있다.
    - `ls -l > result.txt` : cat result.txt를 통해 내용이 저장된 것을 확인가능
    - 해당 기호는 기본적으로 앞에 1이 생략되어 있기 때문에 standard output을 저장하는 방식이다.
    - 만약 standard error를 저장하고 싶다면 2로 지정해야 한다.
    - ex) rename2.txt를 삭제한 후 다시 삭제하는 경우
        - 에러가 발생한다.
        - 해당 내용을 단순히 `>` 를 이용해 다른 파일에 저장하려하면 저장되지 않는다.
        - 왜냐하면 그것은 standard error가 아닌 output을 저장하는 방식이기 때문
        - 따라서, `rm rename2.txt 2> error.log`로 해야 한다. 따라서 아래와 같이 쓴다.
        - `rm rename2.txt > result.txt 2> error.log`
- Input
    - program arguments : control information
    - environment arguments : state information
    - standard input
        - standard input은 keyboard로 사용자가 입력한 내용을 의미한다.        
        - cat 명령어
            - 기존에는 파일의 내용을 보여줬다.
            - 단순히 cat만 쓰고 enter를 누르면 사용자가 keyboard로 input한 내용을 보여준다.
            - 따라서 표준 입력을 받을 수 있는 명령어 이므로 < 를 통해 파일명을 지정할 수 있다.
            - ex)만약, hello.txt에 hello라는 내용만 들어있다고 가정한다.
                - 해당 내용을 보기 위해서 cat hello.txt로 바로 볼 수도 있지만
                - cat < hello.txt로 내용을 볼 수 도 있다. 표준 입력!
        - head 
            - head -n1 linux.txt라고 하면 1줄만 출력한다.
                - 이 방식은 command line argument로 명령어의 인자로 준 것이다.
                - 만약? standard input으로 주고 싶다면??
            - head -n1 < linux.txt로 사용한다.
                - 즉, linux.txt의 내용을 standard input으로 redirection하여 head라는 process의 입력값이 된다.
                - 그렇다면, 위 내용을 결과로 저장하고 싶다면?
            - head -n1 < linux.txt > one.txt
                - 즉, 해당 결과를 one.txt에 저장할 수 있다.
- 지금까지 한 내용처럼 input과 output으로 넘기는 것을 stream이라고 한다. 
### 7. 쉘과 커널
- 쉘
    - 기능 : 사용자의 명령을 shell이 번역하여 kernel에 전달한다., 즉, 커널을 직접 제어할 수 없으므로 사람이 이해하기 쉬운 명령을 해석하여 커널에 전달한다.
    - 여러 가지 종류의 shell이 존재한다. ex) bash, zsh
    - zsh 라고 검색했을 때 안나오면 설치가 안된 것. `sudo apt-get install zsh`로 설치 가능
    - `echo $0`을 통해 현재 사용중인 shell을 알 수 있다.
        > shell은 어디에 위치하고 있을까? `ls /bin`을 해보면 알 수 있다.
        
        > /bin은 linux 운영체제에서 사용하는 기본프로그램이 위치하는 디렉토리이다!, 이전에 사용했던 rm, cat과 같은 명령어도 해당 위치에 파일로 존재한다는 것을 알 수 있다.

    - bash vs zsh
        - zsh는 cd 이후 tab을 누르면 가능한 디렉토리를 보여주는데, 숨김은 보여주지 않음.
        - zsh는 좀 더 편의성이 높다. /home/ubuntu로 이동시 /h/u하고 tab누르면 알아서 변형
        - 디렉토리 이동시 더욱 편의
    - shell script
        - shell에서 실행되는 명령들을 저장해놓을 수 있다.
        - 이를 통해 자동화된 업무를 수행할 수 있다.
        - 실제로 업무 프로세스 상에서는 복잡한 명령 구조를 통해 진행되는 경우가 많은데, 이를 항상 기억해두기보단 필요할 때 마다 저장된 내용을 꺼내서 쓰는 것이 이득일 것.
        - 예시(nano editor로 저장)
            - <pre><code>
                #!/bin/bash         --> #!를 인지하고 해당 내용이 bash로 해석되어야 한다는 것을 인지함
                if ! [ -d bak ]; then --> bak이 디렉토리이며 존재하지 않는다면
                        mkdir bak     --> 만든다.
                fi                    --> if 종료문
                
                cp *.log bak
            </code></pre>
        - 위 스크립트를 실행시에는 `./backup`과 같이 파일이름으로 실행할 수 있다. permission denied가 된다면 권한을 변경하면 된다.
            > `chmod +x backup` : 이를 통해 실행권한을 추가할 수 있다.

    * wild card
        - `*` 를 이용해 사용 만약 a.log, b.log, c.log가 있다고 가정했을 때, *.log라고 하면 확장자가 .log인 모든 파일을 의미(현재 디렉토리에서)
- kernel
    - 하드웨어를 제어하여 명령을 수행한다.
- 왜 커널과 쉘은 분리되어 있을까?? 찾아보자.
### 8. 디렉토리의 구조
- <a href="https://www.thegeekstuff.com/2010/09/linux-file-system-structure">참조</a>
- 각 디렉토리
    - / 
        - root directory, 최상위 디렉토리
    - /bin
        - binary의 줄임말이며 2진수라는 의미이다.
        - 실행가능한 프로그램을 컴퓨터에서는 binary라고도 부른다.
        - 이곳에는 사용자가 실행가능한 명령어 프로그램이 위치한다.
    - /sbin
        - System binaries를 의미한다.
        - 이 또한 바이너리 프로그램이 위치함.
        - system administrator가 사용하는 프로그램이 위치한다. 일반사용자가 이용하는 것은 /bin에 위치
    - /etc
        - 설정파일이다.
        - 대부분의 프로그램의 설정은 파일을 변경하는 곳.
        - 이미 설치된 프로그램, 운영체제의 설정을 건드릴 수 있음.
    - /dev
        - device files
    - /proc
        -  process information
    - /var
        - variable files로 용량이 바뀔 수 있다는 것.
        - 즉, 내용이 변경될 수 있는 파일들이 위치하고 있다.
    - /tmp
        - 임시파일이 저장됨. 종료 후 다시 켜면 다 삭제됨.
    - /home
        - 사용자들의 directory
        - home directory아래에 각 사용자들의 파일이 저장될 수 있도록 각 디렉토리가 존재할 수 있다.
        - 어디에 위치하건 나의 home directory로 이동해야할 경우가 많이 있다.
        - cd /home/ubuntu와 같이도 가능하지만, cd ~를 이용하면 현재 사용자의 home 디렉토리로 한번에 이동가능하다.\
    - /boot
    - /lib
        - /bin과 /sbin에 위치하는 프로그램이 공통으로 사용하는 라이브러리가 위치함.
    - /opt
        - Optional add-on Applications
        - 일반적으로 apt-get을 통해 패키지를 다운로드 받으면 특정 디렉토리에 위치하게 된다.
        - 이 것을 사용자 지정 디렉토리로 설정하고 싶을 때, 애매한 경우 Opt에 놓으면 된다.
    - /mnt
    - /media
    - /srv
    - /usr
        - 사용자 프로그램이 저장되는 디렉토리이며 내부에 아래와 같이 분화되어 있다.
        - /bin
        - /sbin
        - /lib
        - /local
        - 역사적인 맥락에 따라서, 기존에는 필요했던 부분이지만 지금은 거의 통합되어 잘 사용하지 않기도 함.
        - 지금은 home directory에 각 유저의 프로그램이 위치.
### 9. 프로세스
- 하드웨어 상식
    - 컴퓨터의 내부 구조
        - cpu : processor -> 프로그램 처리
        - ram : memory -> 필요 프로그램 적재
        - ssd/hdd : storage --> 가격이 싸며 용량이 큼, 속도는 느림
            - 이 속도로는 cpu의 고속처리 속도를 따라갈수가 없다.
            - 그래서 실행되는 프로그램은 읽어서 메모리에 적재시키고 해당 프로그램을 cpu에서 처리하는 것이다.
        - 위와 같은 기본적인 설계임. process는 ram에 적재되어 실행중인 프로그램을 의미한다.
        - 그리고 그 프로그램을 처리하는 것이 cpu, 즉 processor
- 프로세스 모니터링
    - ps
        - process 리스트를 보여줌
        - `ps aux`라고 하면 background의 모든 실행중인 프로그램을 보여준다.
        - PID : 각각의 프로세스의 식별자이다. 이를 통해 process를 kill가능
             - `sudo kill [pid]`
    - top
        - `sudo top`으로 가능
    - htop
        - top하고 같은데 좀 더 graphical함.
        - 실제 메모리 사용 : RES
        - 실행 시간 : Time+
        - command : 어떤 명령으로 실행되었는가
        - 물리적인 메모리의 크기 : MEM%
        - 위 쪽의 숫자는 cpu들을 의미하며 Mem은 메모리사용 정도임.
        - Load average는 평균 부하를 의미한다. 즉, cpu의 점유율과 관련. 각각 1, 5, 15분간 cpu 점유율 평균치
### 10. 파일을 찾는 방법
- 파일의 용도
    - 데이터 보관, 실행파일(명령을 보관)
- 찾기
    - locate
        - 실행 안되면 `sudo updatedb`를 해주자. 명령어의 위치를 디비에 저장하는 방식이기 때문에 update하지 않으면 찾지 못한다.
        - database를 뒤져서 파일을 찾는다.
        - ex) `locate *.log` : .log 확장자인 모든 파일을 찾는다.
        - locate가 사용하는 데이터베이스를 mlocate라고 부르며 `sudo updatedb`를 수행하면 mlocate의 현재 존재하는 파일들의 정보를 update할 수 있다.(일반적으로 정기적으로 수행되는 명령)
    - find
        - <a href="http://webdir.tistory.com/155">참조</a>
        - 사용법 : find [검색대상위치] [옵션] [수행할작업]
    - whereis
        - `whereis ls` : ls파일이 위치하는 곳을 알려줌.(복수)
            - ls가 존재하는 파일, manual이 존재하는 위치를 알려줌
            - ls가 위치하는 것은 /bin/ls인데 왜 ls만으로 실행할 수 있을까? $PATH때문!
        - $PATH
            - `echo $PATH`를 통해서 확인해보면, 각각의 경로가 지정되어 있는 것을 알 수 있다.(:으로 구분)
            - Unix계열의 운영체제에는 이 값을 기본적으로 가지고 있다.
            - 만약 ls라는 명령어를 실행하면, $PATH라는 변수에 담긴 디렉토리들을 검색하여 그 디렉토리에 ls라는 실행파일이 존재하는곳을 차례대로 뒤진다.
            - 그 뒤진 디렉토리에서 ls라는 파일이 발견되면 그것을 실행할 수 있는 것이다.
            - $PATH는 변경가능하며 특정 디렉토리를 추가하면 그 디렉토리에 있는 파일도 바로 실행가능하다.
            - 이런 변수를 환경변수라고 부른다.
        - whereis --help 혹은 man을 통해 option을 확인할 수 있다.
        