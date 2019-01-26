# 간단한 Vue.js Tutorial!

#### vue.js 란 무엇인가?
    * 프론트 엔드 자바스크립트 프레임 워크
    * 다른 프레임 워크보다 작고 가벼우며, 복잡도도 낮음. 
    * 상대적으로 사용하기 간편하고, 시작도 쉽다.
    * 뷰(view)에만 집중함.

#### vue.js 의 장점
    * 메뉴얼이 다른 프레임 워크나 라이브러리에 비해 한글화가 잘 되어있다.
    * 정리도 잘 되어있어서 시작하기 좋은 환경이다.
    * 성능이 좋다
    * 템플릿을 사용해서 HTML파일에서 바로 사용할 수 있다.
    * _스트리밍 서버 사이드 렌더링_ 지원. 유저들에게 빠르게 결과 반환 가능
     > 렌더링 : 어떤 웹페이지에 접속했을 때, 그 페이지를 화면에 보여주는 걸 렌더링이라고 함.
     보통 서버 사이드 렌더링은 새로운 요청을 했을 때 새로고침을 해야했음. 

#### vue.js 시작할때,
    1. CDN에서 스크립트 파일을 불러오는 방법
    2. 커맨드 라인 인터페이스 사용하여 프로젝트 구성하는 방법

*   *   *
#### JSBin을 통해 vue.js 시작하기
    > JSBin은 브라우저에서 (JS, CSS, HTML)코드를 작성하여 실시간으로 결과를 확인할 수 있음.
    [JSBin] (https://jsbin.com/fivomus/edit?html,output)
    * 상단의 JavaScripts 탭 누루면 JS를 작성할 수 있는 박스가 생겨남
    * Output부분에서 quto-run JS 부분 체크
    
#### vue.js 불러오기
* 상단의 Add Library 버튼을 눌러 제일 최신 버전 받기(업데이트가 바로바로 되지 않아 Vue.js메뉴얼에서 최신버전 CDN 받기 )
[메뉴얼의 서치방법 | CDN 주소 제공(링크 중 unpkg에서 제공하는 링크 사용)] (https://unpkg.com/vue/dist/vue.js)
   
 <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width">
        <title>JS Bin</title>
    </head>
    <body>

        <script src="https://unpkg.com/vue/dist/vue.js"></script>
  
    </body>
    </html>

### 간단한 예제코드 작성해보기
body 태그에서 vue를 불러오기 전에 코드 삽입

##### 1. body 태그에 script 위에 코드 삽입

   <div id = "app">
    <h1>Hello, Vue</h1>
    <div>


##### 2. h1 태그 안의 Vue 부분을 {{ name }} 으로 변경
   
    <h1>Hello, {{ name }}</h1>


##### 3. 자바스크립트 탭을 열어서 다음과 같이 코드 작성 (새로운 뷰를 정의)
<Java Script>
>
   var app = new Vue({  
      el: '#app', //어떤 엘리먼트에 적용할지 정함  
                  //data는 해당 뷰에서 사용할 정보를 지님  
      data: {  
      name : 'Vue'  
      }  
   });

위의 순서대로 진행을 하면 처음에 HTML 코드로 쳤던 'Hello, Vue' 가 뜬다!
> : name의 값을 'Vue'라고 설정했어서 `{{ name }} `부분에 대입 되는 것

##### 4. 콘솔에서 app.name값 변경
상단의 콘솔을 클릭하여 콘솔창을 실행
`app.name = "velopert" ` 로 입력해보면 화면에 바로 값이 바뀌어 렌더링됨

