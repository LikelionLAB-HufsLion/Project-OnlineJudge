도커
===
***
## DOCKER
>Docker는 컨테이너 기반의 오픈소스 가상화 플랫폼.
* Docker는 소프트웨어를 **컨테이너**라는 유닛으로 패키징, 이 컨테이너에는 라이브러리, 시스템 도구, 코드 등 소프트웨어를 실행하는 데 필요한 모든 것이 포함되어 있다.
* 또한 도커를 사용하여 애플리케이션을 신속하게 구축, 테스트 및 배포할 수 있다. 도커의 등장으로 복잡하고 어려웠던 서버관리의 방식이 완전히 달라지게 된다.
* 도커를 이해하기 위해서는 컨테이너와 이미지라는 두 개의 큰 개념으로 살펴보아야 한다.

## 작동방식
>Docker는 컨테이너를 위한 운영 체제.
* 가상 머신이 서버 하드웨어를 가상화하는 방식과 비슷하게 컨테이너는 서버 운영 체제를 가상화한다. Docker는 각 서버에 설치되며 컨테이너를 구축, 시작 또는 중단하는 데 사용할 수 있는 간단한 명령어를 제공함.
* 서버에서 이야기하는 컨테이너는 다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 **프로그램의 배포 및 관리를 단순하게 해준다.**


## 기존의 가상화 방식
>기존의 가상화 방식은 주로 OS를 가상화하였다.
* 우리에게 익숙한 VMware나 VirtualBox같은 가상머신은 호스트OS 위에 게스트OS 전체를 가상화하여 사용하는 방식이다.
* 이러한 방식은 여러가지 OS를 가상화 할 수 있고 비교적 사용법이 간단하지만, 무겁고 느려서 실제 운영환경에선 사용할 수 없다.


## 컨테이너
>기존 가상화와 컨테이너의 차이점 및 특징
* 컨테이너는 격리된 공간에서 프로세스가 동작하는 기술. 가상화 기술의 하나지만 기존방식과는 차이가 있다.
* 하나의 서버에 여러개의 컨테이너를 실행하면 **서로 영향을 미치지 않고 독립적으로 실행**되어 마치 가벼운 VMVirtual Machine을 사용하는 느낌을 준다.
* 실행중인 컨테이너에 접속하여 명령어를 입력하여 패키지를 설치할 수 있으며 사용자도 추가하고 여러개의 프로세스를 백그라운드로 실행할 수도 있다.
* **여러개의 프로그램을 컨테이너를 통하여 손쉽고 빠르게 띄울 수 있다.** -> 서버관리가 용이해진다.

## 이미지
>이미지는 **컨테이너 실행에 필요한 파일과 설정값등을 포함**하고 있는 것.
* 컨테이너는 이미지를 실행한 상태라고 볼 수 있고 추가되거나 변하는 값은 컨테이너에 저장된다.
* 같은 이미지에서 여러개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 컨테이너가 삭제되더라도 **이미지는 변하지 않고** 그대로 남아있다.
* 예를 들어, ubuntu 이미지는 ubuntu를 실행하기 위한 모든 파일을 가지고 있다.
* 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 이것저것 다른것을 설치할 필요가 없다. 이제 새로운 서버가 추가되면 미리 만들어 놓은 이미지를 다운받고 컨테이너를 생성하면 된다.
* Layer 라는 개념을 사용, 굉장히 효율적으로 이미지를 관리할 수 있다.
>관리방식
* 이미지는 url 방식으로 관리하며 태그를 붙일 수 있다.
* 이러한 방식은 이해하기 쉽고 편리하게 사용할 수 있으며 태그 기능을 잘 이용하면 테스트나 롤백도 쉽게 할 수 있다.
***

VM, 도커 실습
---
***
## 가상머신에 설치, 설정(우분투)
> VirtualBox가 게스트 운영체제를 위해 생성한 가상의 컴퓨터.(게스트 운영체제 : VirtualBox로 생성한 가상머신 안에서 동작하는 운영체제)
1. VirtualBox를 사용하기 위해서는 Hyper-V를 비활성화해줘야 한다.
2. CPU의 가상 지원 확인
3. VirtualBox 설치 파일 및 VirtualBox 확장 기능 패키지 다운, 인스톨
4. VM설정 및 우분투 이미지 다운
5. Ubuntu 18.04 VM 설치

## Docker for Windows
> Hyper-V 기능을 이용
* 제어판에서 Hyper-V 기능 활성화한 후 Docker for Windows 설치.

## 컨테이너 실행, Docker 명령어
1. 버전확인 : docker version
2. 도커실행 : docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
3. 자주 사용하는 옵션
* -d 	detached mode 흔히 말하는 백그라운드 모드
* -p 	호스트와 컨테이너의 포트를 연결 (포워딩)
* -v 	호스트와 컨테이너의 디렉토리를 연결 (마운트)
* -e 	컨테이너 내에서 사용할 환경변수 설정
* –name 	컨테이너 이름 설정
* –rm 	프로세스 종료시 컨테이너 자동 제거
* -it 	-i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션
* –link 컨테이너 연결 [컨테이너명:별칭]

## 컨테이너 실행
* docker run ubuntu:16.04 명령어 사용.
* run(사용할 이미지 확인) -> pull(없으면 다운로드) -> create(컨테이너 생성) -> start(시작)
