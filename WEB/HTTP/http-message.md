
아래의 예시를 가지고 http message에 대해 공부해보자 </br>

HTTP 요청 메세지
```
GET/search?q=hello&hl=ko HTTP/1.1 (start-line)
Host: www.google.com              (header)
                                  (CRLF)
``` 

HTTP 응답 메세지
```
HTTP/1.1 200 OK                        (start-line)
Content-Type: text/html;charset=UTF-8  (header)
Content-Length: 3423                   (CRLF)

<html>                                 (message body)
 <body>...<body>
</html>
```

# HTTP 메시지 구조
|HTTP 메시지 구조|
|------|
|start-line 시작 라인|
|header 헤더|
|empty line 공백 라인 (CRLF)|
|message body|

## HTTP 응답 메세지 공식 스펙
<img width="1284" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/eeba0e12-e359-45d2-976d-f1e7ac058a29">

## 시작라인
1. 요청 메세지
```
GET/search?q=hello&hl=ko HTTP/1.1
```
- 위의 한줄은 start-line이다. </br>
- start-line = request-line / status-line 
- request-line = method(공백)request-target(공백)HTTP-version CRLF(엔터) </br>

- method </br>
  GET </br>
  서버가 수행해야 할 동작 지정
- request-target </br>
  /search?q=hello&hl=ko </br>
  absolute-path[?query] (절대경로[?쿼리])</br>
  절대경로 ="/"로 시작하는 경로임
- HTTP-version </br>
  HTTP/1.1

2. 응답 메세지
```
HTTP/1.1 200 OK                        
....
```   
- start-line = request-line/status-line
- status-line = HTTP-version(공백)status-code(공백)reason-pharse CRLF
  
- HTTP-version </br>
  HTTP/1.1
- status-code </br>
  200</br>
  요청 성공, 실패를 나타냄
- reason-pharse </br>
  OK </br>
  이유 문구로 사람이 이해할 수 있는 짧은 상태 코드 설명 글

## HTTP 헤더  
- HTTP 전송에 필요한 모든 부가 정보
- 예를 들어 메시지 바디의 내용 요약, 메시지 바디 크기, 압축, 인증, 요청 클라이언트(브라우저) 정보, 서버 애플리케이션 정보, 캐시 관리 정보 등등
- 표준 헤더가 너무 많다
- 필요시 임의의 헤더를 추가할 수 있다.


HTTP 요청 메세지
```
Host: www.google.com            
``` 

HTTP 응답 메세지
```
Content-Type: text/html;charset=UTF-8 
```
- header-field = field-name ":" OWS field-value OWS (OWS: 띄었기 허용)
- field name은 대소문자 구분이 없다.

## HTTP 메시지 바디
- 실제 전송할 데이터
- HTML 문서, 이미지, 영상, JSON 등등 byte로 표현할 수 있는 모든 데이터를 전송할 수 있다.
