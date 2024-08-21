## 계정 정보 설정

```
git config --global user.name "yourname"
git config --global user.email "yourEmail"
```

## 새로운 Git 저장소 생성

```
git init
```

## 작업 디렉토리상의 모든 변경 내용을 스테이징 영역에 추가

```
git add .
```

## 스테이징 영역에 있는 소스 코드를 로컬 저장소에 간단한 메시지와 함께 저장

```
git commit -m "comment"

* 다시 커밋하기
git commit --amend -m "new comment"
```

## 로컬 git저장소와 github의 remote 저장소 연결

```
git remote add origin "url"
```

## 로컬 깃 저장소에 있는 소스 코드를 깃허브 저장소로 push

```
git push -u origin main

* -u옵션은 현지 브랜치에서 어떤 원격에 어떤 브랜치로 push 할 것 인지 설정 (처음 설정한 브랜치 따라감)
```

## 작업 디렉토리와 스테이징 영역의 상태 표시

```
git status
```

## commit 기록 정보 확인

```
git log
```

## branch 관련

```
* 브랜치 생성
git branch name

* 브랜치 리스트 확인
git branch

* 브랜치 이동
git switch branchName

* 브랜치 생성하면서 이동
git switch -c branchName

* 브랜치 이름 바꾸기
git branch -m branch1 branch2

* 브랜치 삭제
git branch -d branchName

* 브랜치 병합하기
git merge branchName [main branch에서 사용]
git rebase main [main branch가 아닌 곳에서 사용]
```


## 커밋 가져온 후 자동 병합 시도
```
git pull
```

## 현재 브랜치에 존재하지 않는 대상 branch에서 커밋 수집 후 로컬에 저장
```
git fetch
```

## 충돌 처리
```
* 변경 사항 비교 후 선택하여 병합
git config pull.rebase false

* 해당 커밋이후 모두 삭제
git reset --hard (commit hash)

* 해당 커밋만 삭제
git revert (commit hash)
```

## 작업 임시 저장
```
git stash (저장)
git stash list (저장 목록 보기)
git stash pop (불러오기)
git stash clear (저장 목록 전부 삭제)
```
