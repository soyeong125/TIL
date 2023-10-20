# HashMap
- Map 인터페이스를 구현한 Map 컬렉션
- Map 인터페이스를 상속하고 있기 때문에 Map 성질을 그대로 가지고 있다.
- Map은 키와 값으로 구성된 Entry객체를 저장하는 구조를 가지고 있다.
- 키와 값은 모두 객체이다.(키는 중복 불가, 값은 중복 가능)
- 만약 기존에 키가 있는데 동일한 키를 추가한다면, 기존 키는 제거된다.
- HashMap은 이름 그대로 해싱을 사용하기 때문에 많은 양의 데이터를 검색하는데 있어 뛰어난 성능을 보인다.
![image](https://github.com/soyeong125/TIL/assets/57309311/d0ceefbc-cae5-44e3-8213-45e7cbeac398)

## 사용법
### 추가
- put(key,value)


### 삭제
- remove(key) : 특정 키 제거
- clear(): 모든 값 제거

## 값 출력
- map.get(key) : 특정 key 값의 value를 얻을 수 있다.
- entrySet() 사용하기
```
for(Entry<Integer,String> entry : map.entrySet()){
  System.out.println(entry.getKey());
  System.out.println(entry.getValue());
}
```
- keySet() 사용하기
```
for(Integer i : map.keySet()){
  System.out.println(map.get(i));
}
```
