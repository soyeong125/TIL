> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# Http Header
## 일반 정보
- From
  - 유저 에이전트의 이메일 정보
  - 일반적으로 잘 사용되지 않음
  - 검색엔진 같은 곳에서 주로 사용
  - 요청에서 사용
- Referer
  - 이전 웹 페이지 주소
  - A > B 로 이동하는 경우 B를 요청할 때 Referer: A를 포힘해서 요청한다.
  - 유입 경로 분석이 가능
  - 참고로 referer는 referrer의 오타인데 그냥 쓴다고한다.
- User-Agent
  - 유저 에이전트 애플리케이션 정보
  - user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/ 537.36 (KHTML, like Gecko) Chrome/86.0.4240.183 Safari/537.36
  - 클라이언트의 애플리케이션 정보(웹 브라우저 정보, 등등) 통계 정보
  - 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능 요청에서 사용
- Server
  - 요청을 처리하는 오리진 서버의 소프트웨어 정보
  - Server: Apache/2.2.22 (Debian)
  - server: nginx
  - 응답에서 사용
- Date
  - 메시지가 생성된 날짜
  - 응답에서 사용한다.

> 오리진 서버란?
> http 요청을 히면 보통 여러 프록시 서버를 거친다. 그중에 진짜 최종 서버를 오리진 서버라고 한다.

## 특별한 정보
- Host
  - 요청한 호스트 정보(도메인)
  - 예를 들면 Host:www.google.com
  - 요청에서 사용한다. (구글에서 서버에 뉴진스를 검색하겠다)
  - 필수 정보이다.
  - 하나의 IP 주소에 여러 도메인이 적용되어 있을 때
  - 하나의 서버가 여러 도메인을 처리해야할 때 (가상 호스트를 통해 여러 도메인을 한번에 처리할 수 있는 서버 존재 가능, 실제 어플리케이션이 여러개 존재)
  ![image](https://github.com/soyeong125/TIL/assets/57309311/dc456e0c-1a28-4aed-947c-3cd8c35df969)

- Location
  - 페이지 리다이렉션
  - 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면 Location 위치로 자동 이동한다. (리다이렉트 됨)
  - 201 Location 은 요청에 의해 생성된 리소스 URI 이다.
- Allow
  - 현재 많이 구현되어 있진 않다.
  - 허용 가능한 HTTP 메서드
  - 405 (Method Not Allowed)에서 응답에 포함해야한다.
  - Allow: GET, HEAD, PUT
- Retry-After
  - 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간
  - 503 (Service Unavailable) 서비스가 언제까지 불능인지 알려줄 수 있다. (날짜나 초단위 표시)
  - Retry-After: Fri, 31 Dec 1999 23:59:59 GMT 
  - Retry-After: 120
 
## 인증
- Authorization
  - 클라이언트 인증 정보를 서버에 전달
- WWW-Authenticate
  - 리소스 접근시 필요한 인증 방법 정의
  - 401 Unauthorized 응답과 함께 사용한다.
  - WWW-Authenticate: Newauth realm="app",type=1,title="Login to \"apps\"", Basic realm="simple"
