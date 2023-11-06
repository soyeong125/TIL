# @Valid를 이용한 유효성 검증
## @Valid의 개념
@Valid는 JSR-303표준 스펙(자바 진영 스펙)으로써 Bean Validation를 이용해 객체의 제약 조건을 검증하도록 지시하는 어노테이션이다. 

JSR 표준의 Bean Validation 의 특징은 객체의 필드에 달린 어노테이션을 통해 편리하게 검증할 수 있다는 것이다.

- JSR-303: 빈 속성을 검증하기 위한 규칙과 방법론을 정의한 것
- Bean Validation: 인터페이스로 된 명세
- Hibernate Validator: 실제 동작할 수 있도록 구현한 것

Spring에서는 일종의 어댑터인 LocalValidatorFactoryBean이 제약 조건 검증을 처리한다. 이를 이용하기 LocalValidatorFactoryBean을
빈으로 등록해야하는데, SpringBoot에서 의존성 추가를 통해 해당 기능들을 자동으로 설정한다.
```
implementation group: 'org.springframework.boot', name: 'spring-boot-starter-validation'
```
</br>

**간단하게 정리하면 자바는 어노테이션을 통해 객체 속성의 제약조건을 편리하게 검증할 수 있는 기능을 제공해준다. 그리고 그 방법 중 하나가 @Valid이다.**

## 사용방법
1. dto의 필드에 검증 어노테이션을 지정한다.
   
![image](https://github.com/soyeong125/TIL/assets/57309311/67af70c2-1800-4c22-8f4e-010d7b99d08a)

2. 컨트롤러 메소드의 검증할 파라미터에 @Valid를 붙여준다
   
![image](https://github.com/soyeong125/TIL/assets/57309311/dca69d73-0272-488b-a6ae-1d6d9425fa6c)


## 동작원리
1. 클라이언트로부터 http 요청이 들어온다.
모든 요청은 `DispatcherServlet`로 전달된다. 이때 `DispatcherServlet`은 HTTP 요청을 처리하는 프론트 컨트롤러이다. 
2. `DispatcherServlet`은 요청 URL을 기반으로 해당 요청을 처리할 핸들러 메소드를 찾는다.
3. 2번의 과정에서 요청 파라미터는 메소드의 매개변수로 바인딩 되는데, 이때 `HandlerMethodArgumentResolver`가 활성화된다.
4. 예를들어 @RequestBody는 `HandlerMethodArgumentResolver`구현체인 `RequestResponseBodyMethodProcessor`가 요청 데이터를 바인딩 한 후,
`@Valid`로 시작하는 어노테이션이 있을 경우에 유효성 검사를 진행한다.
5. 검증에 오류가 있다면 `MethodArgumentNotValidException` 예외가 발생하게 되고, 디스패처 서블릿에 기본으로 등록된 예외 리졸버인 `DefaultHandlerExceptionResolver
`에 의해 400 Bad Request 에러가 발생한다.
6. 매개변수가 성공적으로 바인딩되고, 유효성 검사가 통과하면, 컨트롤러 메소드가 실행된다.


정리해보면, 컨트롤러의 핸들러 메소드에 @Valid를 붙은 DTO를 파라미터로 받으면, 스프링은 메소드 호출 전에 DTO를 검증한다. 
만약 검증에 실패하면 해당 요청을 유효하지 않은 것으로 간주되고, 오류 메세지와 함께 클라이언트로 응답을 반환할 수 있다.

그렇기 때문에 @Valid는 기본적으로 컨트롤러에서만 동작하며, 기본적으로 다른 계층에서는 검증이 되지 않는다. 다른 계층에서 파라미터를 검증하기 위해서는 @Validated와 결합되어야 한다.

# 헷갈렸던 어노테이션 정리
1. @NotNull
   - 반드시 값이 있어야한다. ""," "은 허용한다.
   - 어떤 type이든 수용한다.
2. @NotEmpty
   - 반드시 값이 존재하고, "" 을 허용하지 않는다. 다만 " "의 입력은 허용한다.
   - type: CharSequence (length of character) Collection (collection size) Map (map size Array (array length)
4. @NotBlank
   - 반드시 값이 존재하고, null, ""," " 모두 허용하지 않는다.




> 출처 </br>
> https://www.baeldung.com/java-validation </br>
> https://mangkyu.tistory.com/174 </br>
> https://tecoble.techcourse.co.kr/post/2020-09-20-validation-in-spring-boot/
