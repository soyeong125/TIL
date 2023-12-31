# JPQL vs Query DSL
이번에 조회 쿼리를 작성하면서 조건은 1개밖에 없어서 동적쿼리는 필요없지만, 테이블 조인을 많이하면서 가독성이 많이 떨어진다고 생각했다.</br>
그리고 JPA를 사용하면서 쿼리문을 작성해야할 때, JPQL 와 Query DSL 중 뭘써야하는지 왜써야하는지 정확한 기준을 갖고 있지 않아서 둘의 차이점을 정리해본다.


## JPQL
- JPA의 일부로 Query를 Table이 아닌 객체(Entity)를 기준으로 작성하는 객체지향 쿼리 언어이다.</br>
- JPQL은 객체를 기준으로 움직이기 때문에, 개발할 때, Table에 매핑되는 객체가 반드시 존재해야한다. 당연히 검색도 Table이 아닌 객체를 대상으로 한다.</br>
- Entity와 속성은 대소문자를 구분한다.</br>
- 별칭 사용은 필수이다.</br>

### JPQL 구현방법
1. EntityManager 활용
2. @Query 애노테이션 사용


### JPQL의 문제점
1. 쿼리를 String 형태로 작성하기 때문에, 개발자 의존적인 형태이다.
2. 컴파일 단계에서 type check가 불가능하다.
3. 2의 문제로 런타임 단계에서 오류를 발견하기 때문에 에러 발생 위험이 있다.


## Query DSL
- 위에 언급한 JPQL에 대한 보완을 위해 나온 것이 Query DSL이다.</br>
- 정적 타입을 이용해서 SQL, JPQL을 코드로 작성할 수 있도록 도와주는 오픈소스 빌더 API이다.</br>
- 모든 쿼리에 대한 내용을 함수 형태로 제공할 수 있다. </br>
- 컴파일 단계에서 type check를 가능하게 하여, 에러 발생 위험을 줄일 수 있다.</br>
- 동적 쿼리를 구현할 수 있다. 조회 조건이 많다면 동적 쿼리를 구현해야한다.</br>

## 그럼 언제 JPQL을 쓰고 언제 QueryDSL을 쓰면 좋을까?
- 동적쿼리인 경우 고민 없이 QueryDSL을 사용한다.
- 조건이 간단한 단순한 쿼리 하나 둘 정도는 JPQL을 사용한다.

> 실무에선 무엇을 쓰는지 판단이 불가하여 아래 링크를 참조해보았습니다.
> https://www.inflearn.com/questions/38771/querydsl%EA%B3%BC-jpql%EC%9D%84-%EC%84%A0%ED%83%9D%ED%95%98%EB%8A%94-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EA%B6%81%EA%B8%88%ED%95%A9%EB%8B%88%EB%8B%A4


