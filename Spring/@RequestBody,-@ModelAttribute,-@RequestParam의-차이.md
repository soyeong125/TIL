@RequestBody, @ModelAttribute, @RequestParam 은 Spring에서 Client로 받은
요청을 객체로 바인딩하기 위해 사용하는 방법이다.

# 1. @RequestParam
1개의 HTTP 요청 파라미터를 받기 위해서 사용한다. @RequestParam은 필수 여부가 true
이기 때문에 반드시 파라미터가 전송되어야 하며, 파라미터가 전송되지 않으면 400에러가 발생한다.

반드시 필요한 값이 아니라면 @RequestParam(required = false)을 설정하면 된다.
defaultValue 옵션을 사용하면 기본값도 지정할 수 있다.

# 2. @RequestBody
클라이언트가 전송하는 Json형태의 HTTP Body를 Java 객체로 변환시켜주는 역할을 한다.

@RequestBody로 받는 데이터는 Spring에서 관리하는 MessageConverter들 중 하나인 MappingJackson2HttpMessageConverter를 
통해 Java 객체로 변환된다. 이는 ObjectMapper라는 클래스를 사용한다. 
물론 데이터 형식이 Json이 아닐 수 도 있다.


> ObjectMapper 동작 과정
> ObjectMapper는 Json 메세지를 자바 객체로 변환하는 과정에서, 객체의 기본 생성자를 통해
> 객체를 생성하고, 내부적으로 Reflection을 사용한다.
> 그래서 반드시 @Setter가 필요한건 아니지만, @Getter나 @Setter 혹은 @JsonInclude
> 등 필드에 있는 변수들의 이름을 찾기 위한 메소드들을 필요로 한다
> 그러므로 기본생성자 + @Getter로 클래스를 구현해주면, @Setter 없이도 바인딩 된다.


# 3. @ModelAttrubute
클라이언트가 전송하는 폼(form)형태의 HTTP Body와 요청파라미터들을 생성자나 setter로
바인딩하기 위해 사용한다.

@ModelAttribute에는 매핑시키려는 파라미터의 타입이 객체의 타입과 일치하는지 등을 
포함하는 다양한 검증 작업이 추가적으로 진행된다.

@ModelAttribute를 사용해서 특정 Parameter 값 만을 가져올 수도 있다. 




> 출처 </br>
> https://mangkyu.tistory.com/72
