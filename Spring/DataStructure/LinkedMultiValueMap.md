# LinkedMultiValueMap
Spring Framework의 일부로 제공되는 자료구조로 MultiValueMap를 구현하는 구현체이다.
각 키마다 여러 개의 값을 가질 수 있는 Map을 나타낸다. 기본적으로 내부에 LinkedHashMap을 사용하여 키의 순서를 유지하며, 각 키에 대한 값은 ArrayList로 관리된다.
주로 Spring 에서 HTTP 요청이나 응답에서 다중 값을 가지는 파라미터나 헤더를 다룰 때 주로 사용한다.

다음과 같은 구조를 가진다. 이때 K는 키의 타입이고, V는 값의 타입이다.
```
Map<K, List<V>>
```

# 특징
1. 순서 보장
   - 키의 삽입 순서가 유지된다.
2. 한 키에 여러 값 저장 가능하다.
   - 각 키는 여러개의 값을 가질 수 있다.

# 예제
```
LinkedMultiValueMap<String, String> map = new LinkedMultiValueMap<>();

map.add("key1", "value1");
map.add("key1", "value2");
map.add("key2", "value3");

System.out.println(map); // {key1=[value1, value2], key2=[value3]}

```




> 출처 </br>
> https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/util/LinkedMultiValueMap.html
