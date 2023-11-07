# Git Conflict란?
개발자들이 브랜치를 따서 작업을 하고 각자 master branch에 merge하게 된다.(우리팀은 develop branch에 merge)

- merge과정에서 파일 이름이 같으면 충돌이 발생한다.
- 파일이 다르면 무조건 자동으로 합쳐준다.
- 파일이 같아도 수정한 부분이 다르면 자동으로 합쳐준다.
- 파일이 같고, 수정한 부분이 같으면 충돌이 발생한다.

# 충돌을 해결하는 방법
## 1. 로컬 develop 브랜치를 이용하여 merge 후, pull request
- 기본적인 방법
- 기존 commit 목록이 사라지고, merge commit 기록만 남는다.
  
```
// 마스터 브랜치로 전환
feature1$ git switch develop

// 원격 마스터 브랜치 최신버전 받아오기
develop$ git pull origin develop

// 다시 작업중인 브랜치로 전환
develop$ git switch feature1

// 최신 버전의 로컬 마스터 브랜치와 병합
feature1$ git merge develop

```


## 2. rebase 후, pull request
- 원격 develop을 최신상태러 만든 후, develop을 base로 해서, 내 브랜치가 마치 develop 커밋 이후에 딴 것 처럼 기록을 조작하는 방법
- 작업 브랜치에 commit이 많지 않고, 깔끔한 commit history를 남기고 싶을 때 사용하기
- 하지만 강제푸시를 하기 때문에, 반드시 팀원들과 협의 후 사용해야한다.
  
```
// 먼저 develop 브랜치를 최신 상태로 업데이트

$ git checkout develop
$ git pull origin develop

// feature1 브랜치로 이동

develop$ git switch feature1

// 원격 develop 기반으로 rebase한다. 이렇게 하면 feature1의 변경사항이 develop 브랜치의 최신 커밋 위에 적용된다.(합쳐짐)

feature1$ git rebase develop

// 충돌을 해결하면서, 계속 rebase를 진행한다.
// rebase 과정 중 충돌이 발생하면, git은 rebase를 일시 중지하고 충돌을 해결하라고 말해준다.

충돌 해결
feature1$ git add <충돌 해결 파일> //생략하면 git은 충돌이 해결되지 않았다고 판단함
feature1$ git rebase --continue

// rebase 완료 후 변경사항을 원격에 강제 push
// 원격 저장소의 히스토리를 로컬 저장소의 히스토리로 덮어쓰게하여, rebase로 인한 변경사항으로 저장

feature1$ git push -f origin feature1


// abort 옵션으로 rebase 작업을 중단할 수 있다.
// rebase를 중단하고 시작 전의 상태로 모든것을 되돌린다. 충돌 해결이 어렵거나 rebase 자체를 중단하고 싶을 때 사용한다.
// 충돌 전의 마지막 안정적인 상태로 HEAD와 작업 디렉토리를 복원한다.
feature1$ git rebase --abort

```

### rebase란?
내 브랜치를 맨 뒤로 보내서 commit history를 깔끔하게 관리할 수 있다
![image](https://github.com/soyeong125/TIL/assets/57309311/519e9ec3-1c64-4464-9c79-211e7c337333)


