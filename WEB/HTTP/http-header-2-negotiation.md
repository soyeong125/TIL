> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.
[http-message](WEB/HTTP/http-message.md)에서 간단하게 알아보았지만 좀 더 딥하게 공부해보자.

# Http
## 협상(콘텐츠 네고시에이션)
클라이언트가 원하는 표현을 서버에게 요청한다. 그럼 서버는 클라이언트에 최대한 맞춰준다.</br>
협상 헤더는 요청시에만 사용한다.</br>

- Accept: 클라이언트가 선호히는 미디어 타입 전달
- Accept-Charset: 클라이언트가 선호하는 문자 인코딩
- Accept-Encoding: 클라이언트가 선호하는 압축 인코딩
- Accept-Language: 클라이언트가 선호하는 자연언어

예를 들어 Accept-Language 적용 전엔 기본 값인 영어로 응답이 갔다.</br>
![image](https://github.com/soyeong125/TIL/assets/57309311/cdf2e1ac-2f24-48b1-a617-cb321aef0aa0)
</br>

Accept-Language 적용 후에 한국어로 요청했다. 그랬더니 서버는 한국어로 응답했다.
![image](https://github.com/soyeong125/TIL/assets/57309311/1ffc2c4b-685b-4521-b779-be87dd9e28fe)
</br>

## 협상과 우선순위 1
- Quality Values(q)값 사용
- 0 ~ 1, 클수록 높은 우선순위
- 생략하면 1이다.
![image](https://github.com/soyeong125/TIL/assets/57309311/9275f06d-b7c6-46dc-b18b-1ea2db5cc67a)
- 예를 들어 이렇게 했다면 우선 순위는 아래와 같다.
1. ko-KR;(q=1)
2. ko;q=0.9
3. en-US;q=0.8
4. en;q=0.7

## 협상과 우선순위 2 
- 구체적인 것이 우선한다.
![image](https://github.com/soyeong125/TIL/assets/57309311/7e06ea24-5618-4b97-ac7f-2a7362438e78)
- 예를 들어 이렇게 했다면 우선 순위는 아래와 같다.
1. text/plain;format=flowed
2. text/plain
3. text/*
4. */*

## 협상과 우선순위 3
- 구체적인 것을 기준으로 미디어 타입을 맞춘다.
![image](https://github.com/soyeong125/TIL/assets/57309311/53ba2788-ad1c-4c30-a00f-82e4226ded27)








