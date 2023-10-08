> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

[http-message](WEB/HTTP/http-message.md)에서 간단하게 알아보았지만 좀 더 딥하게 공부해보자.

- 요청 메세지
```
GET/search?q=hello&hl=ko HTTP/1.1 (start-line)
Host: www.google.com              (header)
(CRLF)            
```                                  
- 응답 메세지
```
HTTP/1.1 200 OK                        (start-line)
Content-Type: text/html;charset=UTF-8  (header)
Content-Length: 3423                   (CRLF)

<html>                                 (message body)
 <body>...<body>
</html>
```

# Http Header (일반헤더)
## Http Header 분류
- General 헤더: 메시지 전체에 적용되는 정보, 예) Connetion: close
- Request 헤더: 요청 정보, 예)User-Agent: Mozilla/5.0 (Macintosh; ..)
- Response 헤더: 응답 정보, 예)Server: 
