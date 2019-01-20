Opensource와 Docker을 이용한 OnlineJudge사이트 만들기
=======================================================
* 사용할 OpenSource : [(https://github.com/QingdaoU/OnlineJudgeDeploy)](https://github.com/QingdaoU/OnlineJudgeDeploy)
* 오픈소스 프로젝트 clone해야함.
    > git의 주소 복사
    > 1. C드라이브에 폴더를 만듦(***ex C:\Qingdao***)<br>
    > 2. cmd를 열어 git명령어 입력 한 후 git이 설치되어있는지 확인<br>
    > 3. **git clone -b 2.0 https://github.com/QingdaoU/OnlineJudgeDeploy.git**
    > 4. 폴더에 프로젝트 파일 생성. 프로젝트 파일로 이동(**cd OnlineJudgeDeploy**)<br>
    > 5. 도커 컨테이너를 구동. 자신의 컴퓨터에서 온라인 저지 사이트 실행(**docker-compose up -d**)<br>
    > 7. 제대로 구동이 되면(4개의 모듈이 돌아갈 것) cmd창을 닫은 후 Docker Quickstart Terminal 실행<br>
    > 8. **Docker-machine ls**명령어로 현재 돌아가는 도커머신 확인<br>
    > 9. 도커 내부 컨테이너 확인(**docker ps -a**로 확인. 받은 opensource가 돌아가는 것을 확인. 여기서 __judge-server__(핵심)은 __API형태__로 사용자가 입력한 소스코드를 채점함.)<br>
    > 10. oj-backend는 클라이언트가 접근할 수 있는 웹서버임.
    > 11. **docker-machine ip**를 입력하여 현재 머신이 어떤 아이피에서 접근 가능한지 확인할 수 있음.(ip 복사한 후 웹에 붙여넣어보기)<br>
    > 12. 관리자 계정의 아이디는 root, 비밀번호는 rootroot (소스 설명 document : [https://docs.onlinejudge.me/#/judgeserver/api](https://docs.onlinejudge.me/#/judgeserver/api))<br>
    > 13. 관리자 계정으로 로그인을 한 후 management에 들어가 문제 출제를 해봄(테스트 케이스 넣는 방법은 document에 나와있음)<br>
    > 14. OnlineJudgeDeploy가 있는 곳에 testcase폴더 하나 만듦. (***ex A+B***)<br>
    > 15. 그 안에 확장자 In, out으로 testcase 입력, 출력 파일을 만듦(ex ***1.In, 1.out, 2.In, 2.out***)<br>
    > 16. 파일을 압축하여 서버의 testcase에 choose File을 선택하여 테스트케이스 집어넣음<br>
