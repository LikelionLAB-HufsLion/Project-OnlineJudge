도커 툴박스를 구동시키는 VirtualBox 분석하기
==========================================

**docker-machine ls**
>현재 설치되어있는 도커 머신을 모두 보여줌, ACTIVE에 현재 작동되고 있는 도커머신 표시
* 이미지를 띄어서 컨테이너를 만듦
* 이 이미지들은 oracle virtualbox에서 자동적으로 확인 가능(아마 default로 자동 설정)
* 도커머신을 설치할떄마다 다른 이미지 파일 설치 후 가상머신 위에서 돌아감.
* 서로 각각 다른 컨테이너 파일을 다룰 수 있음
* 이미지 파일은 최소한의 기능만 갖춘 OS로 돌아감
* C드라이브-사용자-user-.docker-machine-machines 에 들어가면 도커머신을 볼 수 있음
*   *   *
**docker version**
> 현재 설치된 프로그램의 버전 정보를 확인할 수 있음<br>
>(클라이언트와 서버가 나뉘어서 보여줌)<br>
> 컨테이너는 컨테이너 자체에 대한 권한만 갖고있고, host os에 대한 권한은 갖고있지 않음.(독립적)
*   *   *
Docker 실습해보기
=================

### 도커를 실행하는 명령어
> docker run [Options] Image[:Tag|@Digest] [command] [arg...]

* **자주 사용하는 옵션들**
    - -d : 백그라운드 모드<br>
    - -p : 호스트와 컨테이너의 포트를 연결(포워딩)<br>
    - -v : 호스트와 컨테이너의 디렉토리를 연결(마운트)<br>
    - -e : 컨테이너 내에서 사용할 환경변수 설정<br>
    - -name : 컨테이너 이름 설정<br>
    - -rm : 프로세스 종료시 컨테이너 자동 제거<br>
    - -it : -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션<br>
    -link : 컨테이너 연결[컨테이너명:별칭]

* **ubuntu 16.04 container생성**
    - **docker run ubuntu:16.04**
        > run명령어 후에 이미지가 없으면 다운로드(pull)한 뒤 컨테이너 생성(create)하고 시작(start)<br>
        > 컨테이너 정상적으로 실행됐지만 명령어 전달이 없어서 바로 종료됨.<br>
        > 컨테이너는 프로세스라서 실행중인 프로세스가 없으면 컨테이너는 종료된다.<br>
    - /bin/bash 명령어로 ubuntu:16.04 컨테이너 실행<br>
        -docker run --rm -it ubuntu:16.04 bin/bash (컨테이너 실행)<br>
            > cat /etc/issue<br>
            > ls<br>
            > 위 명령어를 쳐보면 컨테이너가 실행됐다는 것을 알 수 있음<br>
            > 컨테이너 내부에 들어가기 위해 bash를 실행하고 키보드 입력을 위해 -it옵션을 주었음<br>
            > 프로세스가 종료되면 컨테이너가 자동으로 삭제되도록 --rm옵션을 추가<br>
            > exit로 bash를 종료하면 컨테이너도 같이 종료<br>

* **redis container**
    > redis는 메모리 기반의 다양한 기능을 가진 스토리지.<br>
    > 6379포트로 통신, telnet명령어로 테스트 할 수 있음<br>
    > redis컨테이너는 백그라운드 모드로 실행하기 위해 -d옵션 추가<br>
    > -p옵션도 추가하여 컨테이너 포트를 호스트의 포트로 연결<br>
    > 백그라운드 모드 옵션이 없으면 foreground로 실행이 되는데 아무 키도 입력할 수 없음. 컨테이너 종료할때 ctrl+c를 눌러 종료
    - **docker run -d -p 1234:6379 redis**
    - **telnet localhost 1234** 

* **MySQL 5.7 container**
    - -e옵션을 이용하여 환경변수 설정하고 -name옵션을 이용해서 컨테이너 읽기 어려운 ID대신 쉬운 이름 부여
    - --name옵션을 생략하면 도커가 자동으로 이름을 지어줌. 유명한 과학자나 해커의 이름과 수식어를 조합하여 랜덤으로 생성
    - **docker run -d -p 3306:3306 \-e MYSQL_ALLOW_EMPTY_PASSWORD=true \--name mysql \mysql:5.7**
     > MY_SQL_ALLOW_EMPTY_PASSWORD의 환경설정 하는 이유 : 패스워드 없이 root 계정을 만들기 위함<br>
     > mysql을 컨테이너 이름으로 할당하고 백그라운드 모드로 띄우기 위해 -d 옵션을 준다
    - mysql -h127.0.0.1 -uroot (linux에서 mysql 확인하기)
