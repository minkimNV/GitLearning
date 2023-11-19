# [Git] 여러 계정으로 Git 사용하기 : ssh key 생성 및 등록

<br><br>
머리 개 아프다.

깃허브 계정을 두개로 쓰려고 하니 이런 문제가 생긴다. 
<br><br>

---

### **글로벌로 설정된 사용자 이름과 이메일 정보 삭제하기**

<br><br>
만약 설정해둔 `--global user.name` & `--global user.email` 이 있다면 삭제해줘야한다.
<br><br>

```bash
git config --global --unset user.name
git config --global --unset user.email
```

<br>

---

### SSH 키 생성

<br><br>
이제 ssh 키를 생성해주자.
<br><br>

```bash

cd ~/.ssh

ssh-keygen -t rsa -b 4096 -C "계정 이름 / 계정 이메일 주소"

# ssh 키 이름 설정 원하는 대로 넣기
# 그 다음은 비밀번호를 설정해주라고 하는데 매번 쳐줘야 하니까 그냥 비밀번호 없이
```

<br><br>
<img width="762" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12 50 06" src="https://github.com/minkimNV/SelfLearning/assets/150657776/55728c91-46fe-400b-a2f0-0fcefadb31e7">
<br><br>

---

### ssh-agent에 ssh-key 추가

<br><br>

```bash
eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_rsa_tomoo56
```

<br><br>
ssh-agent에 ssh-key 추가한다.
<br><br>

---
<br>
계정 수만큼 추가한다. 그러니까 이거 한번 더 반복한다.
<br><br>

### SSH 접속 설정

<br><br>
그 다음은 접속 설정을 명시하기 위해 config 파일을 (없다면 생성한 후) 열어서 아래처럼 입력한다.
<br><br>

```bash
open ~/.ssh/config
```

<br><br>
<img width="654" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1 09 13" src="https://github.com/minkimNV/SelfLearning/assets/150657776/40364f9f-f749-4695-ad6e-c8fa92942caa">

<br><br>
저장 하고 끄기. vi 편집기를 이용한다면 i 누르고 내용 입력 후 esc 누르고 :wq 입력하면 된다.
<br><br>

---

### SSH 접속 테스트

<br><br>
이제 ssh 연결 테스트를 하는데
<br><br>

<img width="650" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1 10 49" src="https://github.com/minkimNV/SelfLearning/assets/150657776/138f3bff-d5fe-4d62-ab23-02213c4c419f">
<br><br>
하 외 않 되? 개빡쳐
<br><br>

### 다시! ssh 접속 테스트!

<br>
<br>

```bash
ssh-add -l
```

<br><br>
ssh-agent가 하나에만 연결되있는 걸 확인할 수 있었다. 그래서 다시 ssh-agent에 ssh 키 등록을 했다.
<br><br>

```bash
# ssh-agent 실행
eval "$(ssh-agent -s)"

# 키 등록
ssh-add ~/.ssh/id_rsa_tomoo56
ssh-add ~/.ssh/id_rsa_minizzz56

# ssh-agent에 등록된 ssh 키 확인
ssh-add -l

# ssh 키 연결 확인
ssh -T git@github.com-naver
	# 결과
	# Hi minkimNV! You've successfully authenticated, but GitHub does not provide shell access.
ssh -T git@github.com-gmail
	# 결과
	# Hi minkim7704! You've successfully authenticated, but GitHub does not provide shell access.
```

<br>
<img width="651" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_1 13 41" src="https://github.com/minkimNV/SelfLearning/assets/150657776/d1a789a4-8368-4e5d-9497-7ad89222559e">
<br>

`~/.ssh/config` 파일에서 각 계정마다 설정해둔 User 이름이 떴다. 연결 확인 성공 ㅠ
<br><br>

---

### 특정 디렉토리 사용자 정보 설정하기

<br><br>
계정별로 디렉토리를 나눈다. 원하는 디렉토리를 만들고 시작하면 된다.
<br><br>

```bash
open ~/.gitconfig

# [user]
# 	name = minkimNV
# 	email = tomoo56@naver.com

[includeIf "gitdir:~/Documents/Github/minizzz56/"]
    path = ~/Documents/Github/minizzz56/.gitconfig

[includeIf "gitdir:~/Documents/Github/tomoo56/"]
    path = ~/Documents/Github/tomoo56/.gitconfig
```

<br>

```bash
vi ~/Documents/Github/tomoo56/.gitconfig

# i 클릭
[user]
	name = minkimNV
	email = tomoo56@naver.com

# esc 키 클릭

# :wq 클릭
```

<br><br>

```bash
vi ~/Documents/Github/minizzz56/.gitconfig

# i 클릭
[user]
	name = minkim7704
	email = minizzz56@gmail.com

# esc 키 클릭

# :wq 클릭
```
<br>

---

### 사용자 정보 설정 잘 됐는지 확인

<br><br>

```bash
cd ~/Documents/Github/tomoo56/

mkdir gitTutorial

cd git Tutorial

git init

git config user.name

git config user.email
```

<br>
<img width="653" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12 12 01" src="https://github.com/minkimNV/SelfLearning/assets/150657776/9af1a444-e47f-4efe-bfd4-e2b82f90ab05">
<br>

사용자 이름과 이메일이 설정한 대로 떴으면 성공
<br>

…? minizzz56 폴더는 안되네..?
<img width="653" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12 14 20" src="https://github.com/minkimNV/SelfLearning/assets/150657776/c2a81a9f-d071-4656-8968-f2f271bf39b1">


<br>
일단 스킵.. 왜냐면 나는 일단 tomoo56 계정에 프로젝트를 올리고 싶은거니까…
<br>

---

### 계정 별 GitHub에 SSH Public key 추가

<br>

```bash
ls -al
```

<br>
생성된 공개키 각 계정마다 파일이 두 개씩 생성된 것을 확인할 수 있다. 그중 확장명이 `.pub` 인 파일의 내용을 복사해준다.
<br>

```bash
# 깃허브에 등록하기 위해 공개 ssh 키 복사하기
pbcopy < ~/.ssh/id_rsa_tomoo56.pub
```

<br>
이제 깃허브로 넘어가서 **Setting > Access > SSH and GPG keys > New SSH key** 로 이동

Title은 원하는대로 쓰고 복사했던 공개 ssh 키를 내용에 쓰고 저장하면 아래처럼 리스트가 뜬다.
<br>

<img width="911" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_12 52 41" src="https://github.com/minkimNV/SelfLearning/assets/150657776/9646a958-3657-467a-9bee-0f04c9339ee9">

<br>
이것도 계정 수만큼 실행해준다.
<br>

