> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# HTTP API 설계 예시
## HTTP API - 컬렉션
### POST 기반 등록
POST 기반 회원 관리 API를 설계하면 아래와 같다.
- 회원 목록 /members -> GET
- 회원 등록 /members -> POST
- 회원 조회 /members/{id} -> GET
- 회원 수정 /members{id} -> PATCH,PUT,POST
- 회원 삭제 /members{id} -> DELETE
</br>

컬렉션이란?
- 서버가 관리하는 리소스 디렉토리
- 서버가 리소스으 URI를 생성하고 관리한다.
- 아래 예시에서 컬랙션은 /members (이미지 파일이 내 문서안에 이미지 안에 날짜 폴더 안에 있는것 처럼)
</br>

- 클라이언트는 등록될 리소스의 URI를 모른다.
- 클라이언트는 그냥 http method랑 /member 이렇게 던지면
- 서버가 내부적으로 회원 등록하고 /members/100 이렇게 컬렉견을 생성함
</br>

- 클라이언트의 요청에 맞게 서버가 새로 등록될 리소스 URI를 생성한다.
```
HTTP/1.1 201 Created
Location: /members/100
```

## HTTP API - 스토어 (파일 관리 시스템)
### PUT 기반 등록
PUT 기반 정적 컨텐츠 관리 및 원격 파일 관리 API 를 설계하면 아래와 같다.
- 파일 목록 /files -> GET
- 파일 등록 /files/{filename} -> PUT
- 파일 조회 /files/{filesname} -> GET
- 파일 삭제 /files/{filename} -> DELETE
- 파일 대량 등록 /files/{filesname} -> POST
</br>

스토어란?</br>
- 클라이언트가 관리하는 리소스 저장소
- 클라이언트가 리소스의 URI을 알고 직접 관리
- 여기서 스토어는 /files
</br>

- 클라이언트가 리소스 URI를 알고 있어야한다.
- 클라이언트가 직접 리소스의 URI를 지정한다.
- 파일 등록 /files/{filename} -> PUT
- PUT /files/star.jpg
  
## HTTP FORM 사용
- 순수하게 HTML, HTML FORM 를 사용할 때 HTTP API를 설계하는 방법에 대해 정리한다.
- 웹 페이지 회원 관리에 사용한다.
- GET, POST만 지원한다. 그래서 제약이 존재한다.
- AJAX와 같은 기술을 사용해서 위의 한계를 극복할 수 있다.
</br>

HTTP FORM을 사용할 땐 GET과 POST 메소드만 사용해야한다는 한계가 있다. 이를 극복하기 위해 동사로 된 리소스 경로를 사용한다.
</br> 이런 동사 리소스 경로를 컨트롤 URI라고 한다. HTTP 메서드로 해결하기 애매한 경우에 컨트롤 URI를 사용한다.
- 회원 목록 /members -> GET
- 회원 등록 폼 /members/new -> GET
- 회원 등록 /members/new, /members -> POST
- 회원 조회 /members/{id} -> GET
- 회원 수정 폼 /members/{id}/edit -> GET
- 회원 수정 /members/{id}/edit, /members/{id} -> POST
- 회원 삭제 /members/{id}/delete -> POST

## 참고하면 좋은 URI 설계 개념 (위의 내용 정리)
1. 문서
   - 단일 개념이다. 파일 하나, 객체 인스턴스, 데이터베이스 row를 뜻한다.
   - 예를 들어 /members/100, /files/start.jpg
2. 컬렉션
   - 서버가 관리하는 리소스 디렉터리이다.
   - 서버가 리소스의 URI를 생성하고 관리한다.
3. 스토어
   - 클라이언트가 관리하는 자원 저장소이다.
   - 클라이언트가 리소스의 URI를 알고 관리한다.
4. 컨트롤러, 컨트롤 URI
   - 문서, 컬렉션, 스토어로 해결하기 어려운 추가 프로세스를 실행한다.
   - 동사를 직접 사용한다.   
