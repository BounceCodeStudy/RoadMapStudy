---
marp: true
---

# Internet

# Html

# CSS 
---

# Internet 
-  전 세계에 걸쳐 원거리 접속이나 파일 전송, 전자 메일 등의 데이터 통신 서비스를 받을 수 있는, 컴퓨터 네트워크의 시스템


---
# Http : Hyper text transfer protocol

- 웹브라우저와 웹서버가 컨텐츠(html, 이미지, 오디오, css, javascript 파일등)을 주고 받기 위해서 사용하는 통신규칙인 HTTP(HyperText Transfer Protocol)

### 브라우저는 웹 서버에서 이동하며(navigate) 쌍방향으로 통신하고 HTML 문서나 파일을 출력하는 그래픽 사용자 인터페이스 기반의 응용 소프트웨어

- 웹 브라우저는 대표적인 HTTP 사용자 에이전트의 하나이기도 하다.
Ex) google,firefox,internet explore

---

# Domain Name System

- 사람이 읽을 수 있는 도메인 이름(예: www.amazon.com)
- 머신이 읽을 수 있는 IP 주소(예: 192.0.2.44)로 변환 IP4 ->IP6 
- 호스트 : 인터넷에 연결된 컴퓨터 하나 하나
- 호스팅 : 이런 컴퓨터를 빌려주는 사업
- 웹호스팅 업체 : 웹서버를 전문적으로 빌려주는 비즈니스 
ex) cafe24,가비아,AWS,GCP 등

---

# Semantic Html

        article	본문
        aside	광고와 같이 페이지의 내용과는 관계가 적은 내용들
        details	기본적으로 표시되지 화면에 표시되지 않는 정보들을 정의
        figure	삽화나 다이어그램과 같은 부가적인 요소를 정의
        footer	화면의 하단에 위치하는 사이트나 문서의 전체적인 정보를 정의
        header	화면의 상단에 위치하는 사이트나 문서의 전체적인 정보를 정의
        main	문서에서 가장 중심이 되는 컨텐츠를 정의
        mark	참조나 하이라이트 표시를 필요로 하는 문자를 정의
        nav         문서의 네비게이션 항목을 정의
        section	문서의 구획들을 정의 (참고)
        time	시간을 정의
---

# CSS

http://flukeout.github.io/

1. Universal Selector : 전체 선택자 *, ns|*, *|*, |*
2. Tag Selector : 태그 선택자 elementname
3. ID Selector : ID 선택자 #idname 
4. Class Selector : 클래스 선택자 .classname
5. Combinator : 결합자는 "A는 B의 자식", "A는 B와 인접 요소"처럼, 두 개 이상의 선택자끼리 관계를 형성
6. Attribute Selector : 속성 선택자 [attr=value]

---

# Layout

1. Floats : when we put images. make layout.
2. Positioning : static(basic), relative, absolute(html standard), fixed(whenever scroll is )
3. Display : inline/block elements 
4. BoxModel : margin, padding, border, contents  
5. CSS GRID : CSS 그리드 레이아웃(Grid Layout)은 페이지를 여러 주요 영역으로 나누거나,크기와 위치 및 문서 계층 구조의 관점에서 HTML 기본 요소로 작성된 콘트롤 간의 관계를 정의
6. FlexBox : 엘리먼트들의 크기나 위치를 쉽게 잡아주는 도구
---

# Responsive design and media Queries

- 반응형 웹은 하나의 웹사이트에서 PC, 스마트폰, 태블릿 PC 등 접속하는 디스플레이의 종류에 따라 화면의 크기가 자동으로 변하도록 만든 웹페이지 접근 기법

- media query는 화면의 종류와 크기에 따라서 디자인을 달리 줄 수 있는 CSS의 기능
특히 최근의 트랜드인 반응형 디자인의 핵심 기술
@media {}

---
- p {   font-size : 50px }
        @media(max-width :786px){
        p {color : red;}
} : 786px 이상일 때 색이 빨강으로 보인다.

미디어 쿼리를 줄 때 CSS의 값이 동일할 경우에는 아래에 있는 속성이 사용된다. 

- .header_dn{PC와 모바일 동일한 디자인}
        @media(min-width : 768px){바뀌는 부분의 디자인만}

- .banner_dn{PC와 모바일 동일한 디자인}
        @media(min-width : 768px){바뀌는 부분의 디자인만}

---

# media 쿼리 종류

- width(뷰포트 넓이) / height(뷰포트 높이)
- aspect-ratio(뷰포트 가로세로비) /orientation(뷰포트 방향) 
- resolution(출력장치 해상도) /scan(출력장치 스캔방법)
- grid(격자와 비트맵 중 출력 장치가 사용하는 화면)
- update (출력장치가 화면을 업데이트 하는 주기)
- overflow-block (블록의 내용이 넘쳤을 때 출력장치가 처리하는 방법)
- overflow-inline(인라인의 내용이 넘쳤을 때 스크롤의 가능 여부)
- hover / color / pointer 
- scriting(스크립트를 사용할 수 있는지 여부) 등등등~

---

- 논리연산자 (and,not,only)를 이용해 복잡한 쿼리를 만들수 있다.

- 1. and : 연산자 다수의 미디어 특성을 조합하여 하나의 미디어 쿼리를 만들 때 사용 ex)@media (min-width: 30em) and (orientation: landscape)
- 2. not : 어떤 미디어 쿼리의 결과가 거짓인 경우 (컬러 디스플레이의 경우 monochrome이나 min-width: 700px 의 미디어 특성에 대응하는 폭이 600px인 스크린) , 이 쿼리 전체에 not 연산자가 적용된 결과는 참 
ex)@media (not(hover)) { ... }
- 3. only : 미디어 특성을 지정하는 미디어쿼리를 서포트하지 않는 낡은 브라우저에 대응하여 특정 스타일을 적용하는것
- 4. , (쉼표) : 하나의 미디어 쿼리가 참이면 스타일 (시트)가 적용 
ex)@media (not (color)) or (hover) { ... }

---

# HTTPS(HyperText Transfer Protocol over Secure Socket Layer) : 보안이 강화된 버전

- HTTPS도 SSL 프로토콜 위에서 돌아가는 프로토콜
- SSL 인증서는 클라이언트와 서버간의 통신을 제3자가 보증해주는 전자화된 문서
- 

---

# HTTP Header : 특정 프로토콜의 기능을 제공하기 위해 담고 있는 최소한의 정보

- 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송
- 대소문자를 구분하지 않는 이름과 콜론 ':' 다음에 오는 값(줄 바꿈 없이)으로 이루어짐.
 값 앞에 붙은 빈 문자열은 무시.
- 개발자도구 - network - 파일
- General 헤더: Via와 같은 헤더는 메시지 전체에 적용
- Request 헤더: User-Agent, Accept-Type와 같은 헤더는 요청의 내용을 좀 더 구체화 시키고(Accept-Language), 컨텍스를 제공하기도 하며(Referer), 조건에 따른 제약 사항을 가하기도 하면서(If-None) 요청 내용을 수정 
- Response header: 위치 또는 서버 자체에 대한 정보(이름, 버전 등)와 같이 응답에 대한 부가적인 정보를 갖는 헤더.

---

# CORS (Cross-Origin Resource Sharing)

- 처음 전송되는 리소스의 도메인과 다른 도메인으로부터 리소스가 요청될 경우 해당 리소스는 cross-origin HTTP 요청에 의해 요청된다.

- 웹 서버에게 보안 cross-domain 데이터 전송을 활성화하는 cross-domain 접근 제어권을 부여한다.

- 웹 애플리케이션은 리소스가 자신의 출처(도메인,프로토콜,포트)와 다를 때 교차 출처 http 요청을 실행


https://gmlwjd9405.github.io/2019/01/28/http-header-types.html

---

- Cache : CPU와 주기억장치 사이에 물리적으로 존재하는 버퍼 형태의 고속의 기억장치를 말한다. (통상, 컴퓨터 메모리 버퍼를 지칭)
- 목적 : CPU와 주기억장치 사이의 속도의 차이를 완화 (메모리 읽기 속도 개선용)

- Cookie : 인터넷 웹 상에서 상태정보를 클라이언트측(인터넷 웹브라우저)에 저장하여, 서버측에서 필요할 때마다 지속성있게 활용하고자 할 때 사용한다. (클라이언트 로컬에 저장되는 키와 값이 들어있는 파일) ex) 비회원시 장바구니
- 목적 : HTTP의 비연결(Connectionless)과 무상태(Stateless)을 보완
웹 브라우저에 서버측에 있는 상태값들을 저장할 수 있게하도록 하여 사용자에 대한 지속적인 상태감시 및 상태참조를 한다.

- Session : 일정 시간 동안 같은 브라우저로부터 들어오는 요청을 하나의 상태로 보고 그 상태를 유지하는 기술이다.
- 즉, 웹 브라우저를 통해 서버에 접속한 이후부터 브라우저를 종료할 때까지 유지되는 상태

---

# API (Application Programming Interface)

- 클라이언트, 서버와 같은 다른 프로그램에서 요청과 응답을 주고 받을 수 있게 만든 체계

- 클라이언트의 관점 CRUD / 서버의 관점
Create  / Post : 올려줘
Read / Get : 불러와줘
Update / Put(전체) Patch(일부) : 바꿔줘
Delete / Delete : 지워줘

- Rest API : Representational State Transfer API
좀 더 체계적으로 API를 관리하고 싶어 만들어진 체계 [비교:GraphQl]

- SDK : Software Development Kit
API를 제공해주는 다른 소프트웨어 

---

- HTTP는 요청 메서드를 정의하여, 주어진 리소스에 수행하길 원하는 행동을 나타낸다.

1. GET는 특정 리소스의 표시를 요청합니다. GET을 사용하는 요청은 오직 데이터를 받음.
2. HEAD는 GET의 요청과 동일한 응답을 요구하지만, 응답 본문을 포함하지 않음.
3. POST는 특정 리소스에 엔티티를 제출
할 때 쓰임.종종 서버의 상태의 변화나 부작용.
4. PUT은 목적 리소스 모든 현재 표시를 요청 payload로 바꿈.
5. DELETE는 특정 리소스를 삭제.
6. CONNECT는 목적 리소스로 식별되는 서버로의 터널을 맺음.
7. OPTIONS은 목적 리소스의 통신을 설정.
8. TRACE는 목적 리소스의 경로를 따라 메시지 loop-back 테스트.
9. PATCH는 리소스의 부분만을 수정

---

# HTTP 상태코드 - Http 요청이 성공적으로 완료되었는지 확인

- 100~ 정보 응답
- 200~ 성공 응답
- 300~ 리다이렉션 메시지
- 400~ 클라이언트 에러 응답 
        404 : 클라이언트가 서버와 통신할 수는 있지만 서버가 요청한 바를 찾을 수 없다
- 500~ 서버 에러 응답

---

# JSON(Javascript Object Notation)

- 클라이언트와 서버 간의 요청과 응답을 할 때는 데이터가 담겨야 하므로 데이터를 넣을 수 있는 기능의 여러가지 형식 중 하나.

- 속성-값 쌍 또는 "키-값 쌍"으로 이루어진 데이터 오브젝트를 전달하기 위해 인간이 읽을 수 있는 텍스트를 사용하는 개방형 표준 포맷 (사전)

- { 중괄호로 시작 / 키 : 값 / 여러 상품 정보는 배열로 불러옴. }
        
    {  "id" : "pjw6670" ,
        "pw" : "sakfaf" 
        "items" : ["a","b","c"]}



