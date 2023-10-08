> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# HTTP 메서드 활용
## 클라이언트에서 서버로 데이터 전송방식 2가지
1. 쿼리 파라미터를 통한 데이터 전송 방식
   - GET
   - 주로 정렬 필터(검색어)
3. 메시지 바디를 통하 데이터 전송 방식
   - POST,PUT,PATCH
   - 회원 가입, 상품 주문, 리소스 등록, 리소스 변경

## 클라이언트에서 서버로 데이터 전송하는 4가지 상황
1. 정적 데이터 조회
   - 이미지, 정적 텍스트 문서
   - 조회 시 GET 메서드 사용
   - 일반적으로 쿼리 파라미터 없이 리소스 경로로 단순하게 조회 가능하다.
2. 동적 데이터 조회
   - 주로 검색, 게시판 목록에서 정렬 필터(검색어) (나는 한국에서 뉴진스를 검색한다. 그러면 나오는 쿼리파라미터)
   - 조회 조건을 줄여주는 필터, 조회 결과를 정렬하는 정렬 조건에 주로 사용한다.
   - 조회 시 GET 메서드 사용
   - GET은 쿼리 파라미터를 사용해서 데이터를 전달한다.
   - 쿼리 파라미터를 기반으로 정렬 필터해서 결과를 동적으로 생성한다.
3. HTML Form을 통한 데이터 전송
- HTML Form 전송은 GET,POST만 지원된다.
- HTML Form submit 시 POST 전송된다.(회원 가입, 상품 주문, 데이터 변경)
    - Content-Type: application/x-www-form-urlencoded 사용
    - form 내용을 메시지 바디를 통해서 전송한다. (key=value, 쿼리 파라미터 형식)
    - 전송 데이터를 url encoding 처리
<img width="624" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/a8acab73-0573-43cb-8643-6fbed4a70a29">

- HTML Form은 GET 전송도 가능하다.
<img width="616" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/5ab008ad-53d5-4154-bfd0-92394d860094">

- Content-Type:multipart/form-data
  - 파일 업로드 같은 바이너리 데이터 전송시 사용
  - 다른 종류의 여러 파일과 폼의 내용 함께 전송 가능(그래서 멀티파트임)
<img width="621" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/d8baa6aa-6559-4b5f-8dd0-d344570f5569">

4. HTTP API를 통한 데이터 전송
   - 회원 가입, 상품 주문, 데이터 변경
   - 서버 to 서버 (백앤드 시스템 통신)
   - 앱 클라이언트 (아이폰, 안드로이드)
   - 웹 클라이언트
     - HTML에서 Form 전송 대신 자바 스크립트를 통한 통신에 사용(AJAX)
     - React,VueJs 같은 웹 클라이언트와 API 통신에 사용
   - POST, PUT, PATCH: 메시지 바디를 통해 데이터 전송
   - GET: 조회, 쿼리 파라미터로 데이터 전달
   - Content-Type: applicatipn/json을 주로 사용한다(사실 상 표준임)
     - TEXT,XML,JSON 등등  










