## Git commit

커밋이란, git 저장소의 디렉토리에 있는 모든 파일에 대한 스냅샷을 기록하는 것.

- 커밋이 저장하는 것: 저장소의 이전 버전과 다음 버전의 변경내역 ("delta"라고도 함)

<br/>

✅ **명령어**

```
git commit
```
<br/>

## Git branch

브랜치: 하나의 커밋과 그 부모 커밋들을 포함하는 작업 내역. 특정 커밋에 대한 참조

<br/>

✅ **명령어: 브랜치 생성**

```
git branch [브랜치명]
```

<br/>

✅ **명령어: 브랜치 이동**

- `checkout` : Git 2.23 이전 사용된 명령어. 브랜치 이동, 생성, 커밋 이동, 파일 되돌리기 여러가지가 가능하기에 헷갈림

```
git checkout [브랜치명]
```

- `switch` : Git 2.23 버전부터 도입된 브랜치 전환 전용 명령어

```
git switch [브랜치명] 
```
<img width="867" height="373" alt="image" src="https://github.com/user-attachments/assets/3c61486a-8bbb-49a6-bfbc-06ebbfcff239" />

<br/>
<br/>

## Git Merge (병합)

두 브랜치 변경사항을 그대로 유지한 채 하나로 합쳐 새로운 merge commit을 생성한다.

<br/>

✅ **특징**

- 실제 작업 흐름 그대로 히스토리 보존
- 충돌 발생 시 한 번만 해결하면 됨
- `develop → main` 병합할 경우 사용
- 이미 push된 브랜치의 경우 사용
- 안전성을 우선 시 하는 팀 협업의 경우 사용

<br/>

✅ **명령어**

현재 체크아웃 된 브랜치에 `[브랜치명]`을 병합한다.

```
git merge [브랜치명]
```

<br/>

## Git Rebase (재배치)

브랜치의 커밋들을 다른 브랜치 위로 다시 쌓아 히스토리를 새로 작성한다. 
merge commit 없이, 선형 히스토리를 생성한다.

<br/>

✅ **특징**

- 히스토리가 깔끔
- 커밋 단위로 충돌이 여러 번 생길 수 있음
- 이미 push한 브랜치에 쓰면 위험
- 로컬 feature 브랜치에서 사용
- PR 올리기 전 히스토리 정리할 경우 사용
- 혼자 사용하는 브랜치에서 사용

<br/>

✅ **명령어**

`rebase`는 붙여야하는 브랜치 쪽에서 명령어 수행

```
git rebase [붙이는 대상 브랜치명] 

// rebase 후에는 보통 아래처럼 진행
git checkout main
git merge bugFix
```

<img width="1196" height="715" alt="image" src="https://github.com/user-attachments/assets/9f422515-d8d8-4d12-a966-fb8ca6bfcd71" />
