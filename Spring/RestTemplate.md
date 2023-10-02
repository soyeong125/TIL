# RestTemplate
Spring의 HTTP 통신 템플릿이다. 객체를 사용하여 Rest 방식의 API를 호출할 수 있는 Spring의 내장 클래스이다.
HTTP 요청 후 Json, xml, String과 같은 응답을 받을 수 있다.
HTTP 프로토콜의 메소드(GET, POST, DELETE, PUT)들에 적합한 여러 메소드들을 제공한다.

*Spring 5.0 이후 부터는 RestTemplate는 deprecated 되었다. (WebClient 사용 지향)*

# RestTemplate 특징
- Spring의 HTTP 통신 템플릿
- HTTP 요청 후 JSON, XML, String 과 같은 응답을 받을 수 있는 템플릿
- Blocking I/O 기반의 동기방식을 사용하는 템플릿
- RESTful 형식에 맞추어진 템플릿
- Header, Content-Tpye등을 설정하여 외부 API 호출
- Server to Server 통신에 사용

> Blocking I/O란?
> I/O 작업이 진행되는 동안 유저 프로세스가 자신의 작업을 중단한채, I/O가 끝날 때까지 대기하는 방식이다.
> ![image](https://github.com/soyeong125/TIL/assets/57309311/e742f37e-a9c2-4174-b2f8-c37edac7a2a1)
> 예시를 들면, 애플리케이션에서 read()를 호출해 커널에 read I/O를 요청하면, read가 끝날 때까지 application은 block 되어 다른 작업을 하지 못한다.
> read I/O 가 끝날 때까지 애플리케이션은 중지상태에 머물러있는 것을 의미한다.
> 출처 : https://etloveguitar.tistory.com/140

# RestTemplate 동작원리
1. 애플리케이션 내부에서 Rest API 를 요청하기 위해 RestTemplate 메서드를 호출한다.
2. RestTemplate은 MessageConverter를 이용해 java object을 request body에 담을 message (예를 들어 JSON) 으로 변환한다.
3. ClientHttpRequestFactory에서 ClientHttpRequest를 받아와 요청을 전달한다.
4. 실질적으로는 ClientHttpRequest가 HTTP 통신으로 요청을 수행한다.
5. RestTemplate가 에러핸들링을 처리한다.
6. ClientHttpResponse에서 응답 데이터를 가져와 오류가 있으면 처리한다.
7. MessageConverter를 이용해 response body의 message를 java object으로 변환한다.
8. 결과를 애플리케이션에 돌려준다.
![image](https://github.com/soyeong125/TIL/assets/57309311/495a5a3d-11ca-45b9-a843-31296efea9bd)
- RestTemplate는 통신과정을 ClientHttpRequestFactory(ClienttHttpRequest, ClientHttpResponse)에 위임한다.
- 
   


 
