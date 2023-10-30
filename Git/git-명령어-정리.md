
## git 브랜치 전략을 통한 feature 브랜치 생성 및 push 과정
```
# feature 브랜치 생성(issue 제목과 동일한 브랜치 생성)
(develop)$ git checkout -b Feature/#1-이슈-이름
(Feature/#1-이슈-이름)$

# 소스 코드 변경 작업 후 staging 상태로 변경
(Feature/#1-이슈-이름)$ git add .

# 소스 코드 커밋
(Feature/#1-이슈-이름)$ git commit -m '커밋 메세지'

# develop 브랜치로 checkout(이동)
(Feature/#1-이슈-이름)$ git checkout develop
(develop)$

# Feature/#1-이슈-이름 브랜치 merge
(develop)$ git merge Feature/#1-이슈-이름

# remote repository에 push (Feature/#1-이슈-이름 브랜치에 대해서)
(develop)$ git checkout Feature/#1-이슈-이름
(Feature/#1-이슈-이름)$ git push origin Feature/#1-이슈-이름

# develop 브랜치로 다시 checkout
(Feature/#1-이슈-이름)$ git checkout develop

# Feature/#1-이슈-이름 브랜치 삭제
(develop)$ git branch -d Feature/#1-이슈-이름

```

## 브랜치 관련 기타 명령어
```
// 브랜치 강제 삭제
(develop)$ git branch -D Feature/#2-이슈-이름

// 브랜치명 변경하기
(develop)$ git branch -m Feature/#2-이슈-이름 Feature/#2

// 현재 등록된 브랜치 확인하기
(develop)$ git branch

// 현재 checkout한 브랜치를 기준으로 merge한 브랜치 목록 확인
(develop)$ git branch --merged

// 현재 checkout한 브랜치를 기준으로 merge하지 않은 브랜치 목록 확인
(develop)$ git branch -no-merged
```
