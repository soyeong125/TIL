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

# Http Header
# 과거 RFC2616 표준 (현재 폐기됨)
## Http Header
헤더 안에 있는 내용을 자세히 나눠보면 아래와 같다.</br>
<img width="372" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/688548ab-2e68-4f17-ba64-62148877cdf8">

- General 헤더: 메시지 전체에 적용되는 정보, 예) Connetion: close
- Request 헤더: 요청 정보, 예)User-Agent: Mozilla/5.0 (Macintosh; ..)
- Response 헤더: 응답 정보, 예)Server:Apache
- Entity 헤더: 엔티티 바디 정보, 예)Content-Type: text/html, Content-Length: 3424

## Http Body
<img width="392" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/927d5cbf-c7d9-4e12-95c2-7020badeafc4">
</br>

- 메세지 본문은 엔티티 본문을 전달하는데 사용
- 엔티티 본문은 요청이나 응답에서 전달할 실제 데이터
- 엔티티 헤더는 엔티티 본문의 데이터를 해석할 수 있는 정보를 제공한다.(데이터 유형이나 html, json, 데이터 길이, 압축 정보 등등)

# RFC723x 표준
과거 RFC2616 표준이 폐기되고 RFC7230 ~ 7235가 등장했다.</br>

## 변경 사항
- 엔티티(Entity) -> 표현(Representation)
- 표현으느 표현 메타데이터와 표현 데이터로 이루어져있다.

## Http Body
<img width="389" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/cab4870e-77fc-48ea-8be9-baafa59f884c">
</br>

- 메시지 본문을 통해 표현 데이터 전달
- 메시지 본문 = payload (페이로드)
- 표현은 요청이나 응답에서 전달할 실제 데이터이다.
- 표현 헤더는 엔티티 본문의 데이터를 해석할 수 있는 정보를 제공한다.(데이터 유형이나 html, json, 데이터 길이, 압축 정보 등등)
- 참고로 표현 헤더는 표현 메타데이터와 페이로드 메시지를 구분해야하지만 여기선 생략함

## 표현
- 표현 헤더는 전송, 응답 둘다 사용한다.
- Content-type
  - 표현 데이터 형식
  - 미디어 타입, 문자 인코딩
  - 예) text/html;charset=utf-8, application/json, image/png
- Content-Encoding
  - 표현 데이터 압축 방식
  - 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가
  - 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제
  - 예) gzip, deflate, identify
    <img width="275" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/7c7b735b-8a65-43fe-b29d-e10e4b188d88">

- Content-Language: 표현 데이터의 자연언어
- Content-Length: 표현 데이터의 길이
