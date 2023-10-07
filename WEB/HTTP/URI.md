> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# URI (Uniform Resource Identifier)
- URI
Locator, Name 또는 둘 다 추가로 분류될 수 있다.
- URL
Locator, 리소스가 있는 위치를 지정한 것이다. 위치는 변할 수 있다.
- URN
Name, 리소스에 이름을 부여한 것이다. 이름은 변할 수 없다. </br>
하지만 URN 이름으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않았다.

<img width="788" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/dcf5b81e-9437-4f9e-8095-3d3431e2b47b">
<img width="1178" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/14968dcb-c76a-440e-ae35-c6892fa16df6">

## URL 전체 문법
- https://www.google.com:443/search?q=hello&hl=ko
- scheme://[userinfo@]host[:port][/path][?query][#fragment]

- scheme : http
- host : www.google.com
- port : 443
- /path : /search
- ?query : q=hello&hl=ko

### scheme
- 주로 프로토콜을 사용한다. (http, https, ftp 등등)
- 이미 정해진 포트는 생략 가능하다 (80같은거)

### userinfo
- URL에 사용자정보를 포함해서 인증한다.
- 거의 사용하지 않음

### host
- 호스트명
- 도메인명 또는 IP 주소를 직접 사용가능하다.

### path
- 리소스 경로(path), 계층적 구조
- 예를 들어 /home/file1.jpg 같은 것

### query
- key = value 형태
- ?로 시작하고 &로 추가 가능하다. ?keyA=valueA&keyB=valueB
- 쿼리 파라미터나 쿼리 스트링으로 불린다. 웹서버에 제공하는 파라미터, 문자 형태이다.

### fragment
- https://docs.spring.io/spring-boot/docs/current/reference/html/getting-
started.html**#getting-started-introducing-spring-boot**
- html 내부 북마크등에 사용한다.
- 서버에 전송하는 정보가 아니다.
