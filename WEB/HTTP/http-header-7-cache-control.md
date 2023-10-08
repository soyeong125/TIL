> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# Http Header
## Cache-Control
캐시 지시어(directives)
- Cache-Control: max-age
  - 캐시 유효 시간, 초 단위
- Cache-Control: no-cache
  - 데이터는 캐시해도 되지만, 항상 오리진 서버에 검증하고 있음
- Cache-Control: no-store
  - 데이터에 민감한 정보가 있으므로 저장하면 안됨  (메모리에서 사용하고 최대한 빨리 삭제)

## Pragma
- 캐시 제어 (하위 호환)
- Pragma: no-cache
- HTTP 1.0 하위호환
  
## Expires
- 캐시 만료일 지정 (하위 호환)
- 캐시 만료일을 정확한 날짜로 지정
- HTTP 1.0 부터 사용
- 지금은 더 유연한 Cache-Control: max-age 권장
- Cache-Control: max-age 와 함께 사용되면 Expires는 무시된다.

## 프록시 캐시
![image](https://github.com/soyeong125/TIL/assets/57309311/740cfe7b-50b3-41dc-a002-4b582bebca54)

- Cache-Control: public
  - 응답이 public 캐시에 저장되어도 됨
- Cache-Control: private
  - 응답이 해당 사용자만을 위한 것임, private 캐시에 저장해야 함(기본값)
  - 예를 들어 내 로그인 정보 같은거
- Cache-Control: s-maxage
  - 프록시 캐시에만 적용되는 max-age
- Age: 60 (HTTP 헤더)
  - 오리진 서버에서 응답 후 프록시 캐시 내에 머문 시간(초)

## 캐시 무효화
진짜 캐시하면 안되는 정보에 사용한다.
- Cache-Control: no-cache
  - 데이터는 캐시해도 되지만, 항상 오리진 서버에 검증하고 사용
  - 오리진 서버에 접근이 실패하더라도 캐시 서버 설정에 따라서 프록시 캐시에 있는 캐시 데이터를 반환할 수 있음 (오류보다 옛날데이터가 낫다)
- Cache-Control: no-store
  - 데이터에 민감한 정보가 있으므로 저장하면 안됨  (메모리에서 사용하고 최대한 빨리 삭제)
- Cache-Control: must-revalidate
  - 캐시 만료후 최초 조회시 오리진 서버에 검증해야함
  - 오리진 서버 접근 실패시 반드시 오류가 발생해야함 (504(Gateway Timeout)) (무조건 안됨 1년전 통장 계죄 못보여줌)
  - must-revalidate는 캐시 유효 시간이라면 캐시를 사용함
- Pragma: no-cache (HTTP 1.0 하위 호환)
  
