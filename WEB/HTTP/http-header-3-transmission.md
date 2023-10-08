> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

[http-message](WEB/HTTP/http-message.md)에서 간단하게 알아보았지만 좀 더 딥하게 공부해보자.

# Http Header
## 전송 방식
## 단순 전송
- Content-Length
- 컨텐츠의 길이를 알 때 사용한다. 요청을 하면 그냥 서버는 제공한다. 한번 요청히면 한번에 쭉 받는 방식.
![image](https://github.com/soyeong125/TIL/assets/57309311/2d1c341a-81fb-41f5-83aa-9109672ff574)

## 압축 전송
- Content-Encoding
- content-encoding을 추가로 보내준다.
![image](https://github.com/soyeong125/TIL/assets/57309311/999d6fce-a630-420d-b6ef-ec4741497c54)

## 분할 전송
- Transfer-Encoding
- 전송할 데이터의 용량이 큰데 한번에 보내면 대기시간이 길 것 같을 때 사용한다. 클라이언트는 일부만 받을 수 있음 </br>
데이터 전송이 끝나면 마지막에 0을 전송한다. </br>
![image](https://github.com/soyeong125/TIL/assets/57309311/fa513b93-356e-425e-a06e-5edf915bf526)

## 범위 전송
- Range, Content-Range
- 범위를 지정해서 요청할 수 있다.
- 그래서 이미지를 받을 때 중간에 절반정도 끊기고 다시 요청할 때 사용한다.(여기까지 받았으니까 나머지를 줘!)
![image](https://github.com/soyeong125/TIL/assets/57309311/4a268295-c815-4538-8f6f-2c2644981eaf)
