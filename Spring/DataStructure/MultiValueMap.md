# MultiValueMap
SpringFramework에서 제공하는 인터페이스이다. (자바 아님)
하나의 키가 여러개의 값을 가질 수 있는 Map을 나타내고 기본적으로 아래과 같은 구조를 가진다.

```
Map<K, List<V>>
```

K는 키 타입이고, V는 값의 타입이다.

# 특징 
1. 한 키에 여러값이 매칭될 때 사용
   - 각 키는 여러 개의 값을 가질 수 있다.
   - 예를 들어 HTTP 헤더에 한 키에 여러 값을 가질 수 있는 데이터를 표현할 때 유용하다.
2. 값 추가
   - 'add' 메서드를 사용해서 키에 값을 추가할 수 있다. 만약 해당 키에 값이 있으면 새로운 값이 리스트에 추가된다.
3. 값 가져오기
   - getFirst 메서드를 사용하면 키에 연결된 값들 중 첫번째 값을 가져올 수 있다.

# 구현체 종류
- HttpHeaders
- LinkedMultiValueMap
- MultiValueMapAdapter
- StompHeaders
- WebSocketHttpHeaders   
   


> 출처 </br>
> https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/util/MultiValueMap.html
