> 모든 개발자를 위한 HTTP 웹 기본 지식 - 인프런 강의를 듣고 정리한 내용입니다.

# Http Header
## Cache
- 캐시가 없다면?
  - 데이터가 변경되지 않아도 클라이언트가 요청하면 계속 네트워크를 통해서 데이터를 다운로드 받아야한다.
  - 브라우저 로딩 속도 느림 + 느린 사용자 경험
- 캐시 적용
  - 서버가 응답을 보낼 때 cache-control 이라는 캐시 유효시간을 함께 보낸다. 그러면 사용자의 브라우저 캐시에 데이터가 저장되고 두번째 요청시 유효시간 내에 있다면 브라우저 캐시에서 조회한다.
  - 캐시 덕분에 캐시 가능 시간 동안 네트워크를 사용하지 않아도 된다. (비용 절약)
  - 브라우저 로딩 속도 빠름 + 빠른 사용자 경험
![image](https://github.com/soyeong125/TIL/assets/57309311/5ab44944-5f11-4716-b06e-8b88be228ff5)
![image](https://github.com/soyeong125/TIL/assets/57309311/0dd009ca-fb08-4ecb-bd49-b188f54db8ba)
![image](https://github.com/soyeong125/TIL/assets/57309311/e5a85040-e2ae-4d5e-ba1d-5fb4c5cd45eb)
![image](https://github.com/soyeong125/TIL/assets/57309311/83ac77f4-b7d4-46a4-88b8-6c336f205fcc)

- 캐시 유효시간이 초과된다면?
  - 브라우저 캐시에 담긴 데이터를 더이상 사용할 수 없기 때문에 서버에 다시 요청을 보낸다.
  - 그 후 캐시를 갱신한다. (다시 받는다는 뜻)

## 검증 헤더
- 캐시시간이 초과해서 데이터를 갱신해야하지만, 데이터가 변경되지 않은 경우는 굳이 다시 다운로드 할 필요가 없다.
- 이때 클라이언트의 데이터와 서버의 데이터가 같다는 사실을 확인할 수 있는 방법이 필요하다.
- 검증 헤더로 이를 확인할 수 있다.
- 클라이언트가 요청을 보내면 응답에 데이터가 마지막에 수정된 시간을 포함해서 받는다.
- 응답 결과를 캐시에 저장할 때 데이터와 최종 수정일을 함께 저장한다.
![image](https://github.com/soyeong125/TIL/assets/57309311/4ec32819-8edd-476f-b7e3-bbfe151d204f)
</br>

- 캐시 시간이 초과되었다면 요청에 클라이언트 캐시가 가지고 있는 데이터의 최종 수정일을 포함해서 보낸다.
![image](https://github.com/soyeong125/TIL/assets/57309311/481c1b72-0fa2-49f1-b16f-9a2bb0b12a51)

- 데이터가 수정되지 않았다면 body는 전송하지 않는다.
![image](https://github.com/soyeong125/TIL/assets/57309311/7839f765-c56d-45c1-a094-5edd4bf81114)
- 캐시가 갱신된다.
![image](https://github.com/soyeong125/TIL/assets/57309311/27a95bb3-d278-4cd8-9597-8c7eb12b4607)
