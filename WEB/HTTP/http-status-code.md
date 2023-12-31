> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# 상태코드
클라이언트가 보낸 요청의 처리 상태를 응답에서 알려주는 기능이다.

## 1xx (Informational)
- 요청이 수신되어 처리중이다.
- 거의 사용하지 않는다.

## 2xx (Successful)
- 요청 정상 처리, 성공했다.
- 200 OK
- 201 Created
  - 요청해서 새로운 리소스가 생성됨. 생성된 리소스는 응답의 Location 헤더 필드로 식별 가능)
- 202 Accepted
  - 요청이 접수되었으나 처리 완료 안됨
  - 배치 처리 같은 곳에서 사용됨 (접수 후 1시간 뒤에 배치 돌리겠음)
- 204 No Content
  - 서버가 요청을 성공적으로 수행했지만, 응답 페이로드 본문에 보낼 데이터가 없음
  - 웹 문서 편집기에 임시 저장 버튼 눌러도 아무 내용 없어도 된다.
  - 그냥 같은 화면 유지해야하기 때문에 결과 값이 없어도 된다.

## 3xx (Redirection)
- 요청을 완료하려면 유저 에이전트의 추가 행동이 필요하다.
- 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면 Location 위치로 자동 이동한다.(리다이렉트)
<img width="559" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/1ce2af12-a4a9-4162-a99d-37ed3515f880">
</br>

- 리다이렉션의 종류 3가지
1. 영구 리다이렉션 : 특정 리소스의 URI가 영구적으로 이동했다.
  - 특정 이미지의 위치가 서버내에서 아예 변경된 경우이다. 이전의 URL은 아예 사용하지 않는다.
  - 검색 엔진에서 사용하는 URL을 변경해야한다.
  - 301, 308
  <img width="556" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/3bcdf18f-5ed7-4532-ae43-2f54b6869fe8">
  <img width="603" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/98bf013e-8ace-4629-9603-b8462bf9dabd">

2. 일시 리다이렉션 : 일시적인 변경이다.
  - 검색 엔진에서 사용하는 URL을 변경하면 안된다.
  - 주문 완료 후 주문 내역 화면으로 이동
  - PRG : Post/Redirect/Get (클라이언트에서 한번 막아주는 기술)
  - 302,307,303
  - 302가 모호하기 때문에 303과 307이 등장했지만 이미 많은 실무에서 302를 기본값으로 쓰고 있음
  - 자동 리다이렉션 시 GET으로 변해도 되면 그냥 302를 써도 상관없음
3. 특수 리다이렉션 : 결과 대신 캐시를 사용한다.
</br>

- 300 Multiple Choices
  - 안씀
- 301 Moved Permanently
  - 리다이렉트 시 요청 메서드가 GET으로 변할 수 있음 + 본문이 제거될 수도 있음
- 302 Found
  - 리다이렉트 시 요청 메서드가 GET으로 변하고 본문이 제거될 수도 있음
- 303 See Other
  - 302과 기능이 같다.
  - 리다이렉트 시 요청 메서드가 GET으로 변한다.
- 304 Not Modified
  - 캐시를 목적으로 사용된다.
  - 클라이언트에게 리소스가 수정되지 않았음을 알려준다.
  - 따라서 클라이언트를 로컬 PC에 저장된 캐시를 재사용한다.(캐시로 리다이렉트됨)
  - 응답 메세지에 바디를 포함하지 않음(로컬 캐시 써야하니까)
  - 조건부 GET, HEAD 요청시 사용한다.
- 307 Temporary Redirect
  - 302과 기능이 같다.
  - 리다이렉트 시 요청 메서드와 본문을 유지한다. (절대로 요청 메서드 변경하면 안됨)
- 308 Permanet Redirect
  - 301과 기능이 같다.
  - 리다이렉트 시 요청 메서드와 본문을 유지한다. (처음 POST로 보내면 리다이렉트도 POST)
  - 거의 사용하지 않는다.

## 4xx (Client Error)
- 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음
- 오류의 원인은 클라이언트이다.

- 400 Bad Requset
  - 요청 구문, 메시지 등등 오류
  - 클라이언트가 요청 내용을 다시 검토하고 보내야한다.(파라미터나 API 스펙 확인)
- 401 Unauthorized
  - 클라이언트가 해당 리소스에 대한 인증이 필요함
  - 401 오류 발생시 응답에 WWW-Authenticate 헤더와 함께 인증 방법을 설명한다.
- 402 Forbidden
  - 서버가 요청을 이해했지만 승인을 거부함
  - 주로 인증 자격 증명은 있지만 접근 권한이 불충분한 경우
- 404 Not Found
  - 요청 리소스가 서버에 없음
  - 클라이언트의 권한 부족으로 리소스에 접근할 때 해당 리소스를 숨긴 경우

## 5xx (Server Error)
- 서버 오류, 서버가 정상 요청을 처리하지 못함
- 애해하면 500 오류

- 503 Service Unavailable
  - 서비스 이용 불가
  - 서버가 일시적 과부하 또는 예정된 작업으로 잠시 요청을 처리할 수 없는 경우
  - Retry-After 헤더 필드로 얼마뒤 복구되는지 보낼 수 있다.
