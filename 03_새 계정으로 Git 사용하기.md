# [Git] 새 계정으로 Git 사용하기

<br><br>
`Github` 계정을 새로 만들었을 경우, 새로 만든 계정으로 스위치해서 `git commit`, `git push` 명령을 실행해야 한다.

하지만 기존의 계정 정보(credentials)가 로컬 머신에 저장되어 있기 때문에 `git` 명령을 실행하면 예전 사용하던 계정으로 이벤트가 기록된다.

그러므로 이전 계정의 정보(credentials)을 삭제하고 새로운 계정을 추가해야 한다. 

완전 새 계정이라면 
<br><br>

```bash
git config --global user.name
git config --global user.email
```

<br><br>
이렇게 해주는 것만으로 괜찮다 . ([Git 설치 & GitHub Desktop 설치](Git%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20&%20GitHub%20Desktop%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%207e8c3920c4ba4f8bad2ed356fb6a4be5.md))

macOS에서는 git의 계정 정보(credentials)가 KeyChain 툴에 저장 되므로 이걸 삭제해주어야 한다.
<br><br>

```bash
git credential-osxkeychain erase
host=github.com
protocol=https
```

<br><br>
입력하면 아무 것도 안뜬다. **[키체인 접근]** 이라는 어플리케이션에 들어가서 github을 검색해보자. 아무것도 안뜨면 잘 삭제 된 것.

이제 유저 네임과 이메일 수정해주자.
<br><br>

```bash
git config --global user.name
git config --global user.email
```
