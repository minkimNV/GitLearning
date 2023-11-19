# Git 설치 & GitHub Desktop 설치
<br>
<br>
homebrew가 있다면 git을 설치하기 위한 준비는 다 끝났다. 터미널에서 아래와 같은 명령어를 입력한다.
<br>
<br>

```bash
brew install git
```

<br>
<br>
설치가 완료되면
<br>
<br>

```bash
git --version
```

<br>
<br>
버전 확인을 해주자.
<br>
<br>

---
<br>
<br>
GitHub은 Git 저장소를 호스팅하고 개발자들 간에 협업할 수 있는 기능을 제공하는 웹서비스다.

GitHub Desktop은 GitHub와 연동된 Git 저장소를 GUI으로 관리할 수 있게 도와주는 Git 클라이언트.

Git은 기본적으로 커맨드라인 명령어라서 잘 활용하기 위해서는 커맨드라인 환경 작업에 익숙해야하고, OpenSSH를 사용한 인증 방식을 이해해야하는 번거로움이 있다.

GitHub Desktop을 사용하면 GUI를 통해 직관적으로 Git 저장소의 상태를 확인하고 GitHub 작업을 할 수 있으며, SSH 키 없이도 웹 인증 방식으로 GitHub를 작업을 할 수 있으니까

이제 GitHub Desktop을 설치한다.
<br>
<br>

```bash
brew install --cask github
```

<br>
<br>
Git에서 사용할 이름과 Email을 지정해야한다. git 명령어로 해보자.
<br>
<br>

```bash
git config --global user.name "your name"

git config --global user.email "your email@email.com"
```

<br>
<br>
아 근데 나 새 계정으로 Git 하려는거라  이렇게만 이름과 이메일을 설정해주면 기존 계정 정보가 로컬에 저장되어 있어서 git 명령을 실행할 때 예전 계정으로 이벤트가 기록된다. 
<br>
<br>

```bash
cat ~/.gitconfig

# 위 명령어 입력 후 아래 내용 추가하기

**[user]
		name = your name
		email = your email**
```

<br>
<br>
이제 로컬에서 Git 커밋할 때면 항상 이 정보가 기본적으로 사용된다.
<br>
<br>

---

### 간단 예제

1. Git 저장소 생성: **GitHub Desktop > Create a new Repository > 이름설정 > Create**
    - 나는 GitTutorial 레포지토리를 생성했다.
    - git CLI 명령어를 이용해 생성된 레포지토리로 이동 후 해당 레포지토리에서 Git 초기화 해준다.
    
    ```bash
    cd ~/Documents/GitHub/GitTutorial
    
    git init
    ```
    
    - 해당 레포지토리에서 Git을 초기화 해주어야 Git을 사용할 수 있는 레포지토리가 된다.
2. 텍스트 에디터 설치: VS Code가 설치되어 있으면 생략하고 넘어간다.
3. 브랜치 생성 및 전환: **Current Branch > New Branch > 브랜치 이름 설정 > Create**
    
    <img width="1072" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6 23 36" src="https://github.com/minkimNV/SelfLearning/assets/150657776/048e26ab-c27a-4ff7-a567-f573dd9eec74">

    - Git CLI 명령어를 이용해 브랜치 전환을 해준다. 아래 명령어를 입력하면 새로 생성한 브랜치로 브랜치가 reset되었다고 결과가 나온다.
    
    ```bash
    git switch -C new-branch
    ```
    
4. README.md 편집: Open Editor를 클릭해 사용하는 에디터에서 편집하면 된다. 
    
    <img width="1245" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6 31 06" src="https://github.com/minkimNV/SelfLearning/assets/150657776/6c6ad3d7-a514-4541-a87a-f331beb02c86">

    이렇게 에디터에서 수정을 하면 아래 GitHub Desktop에서 수정사항을 확인할 수 있다.

    <img width="1072" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6 31 18" src="https://github.com/minkimNV/SelfLearning/assets/150657776/9c92639b-a46b-493a-9dde-a0abe1cfde54">
 
5. 수정 내용 커밋: 위 수정사항을 Git저장소에 커밋하자. 지금은 파일 하나만 수정했기 때문에, README.md 파일만 보인다. 여러 파일을 수정한 경우 특정 파일의 수정사항만 커밋하는 것 가능하다.
    
    ```bash
    git add README.md
    git commit -m 'AddNewLine'
    ```
    
    AddNewLine은 커밋라인으로 변경가능하다.
    
    여기까지 진행하고 GitHub을 봤는데 아무것도 없다고 놀라지 말기..ㅎ
    
    지금가지 로컬 Git 저장소에서 일어난 일이기 때문에 이 Git저장소에 저장된 내용은 GitHub저장소와 연동해야한다.
    
    커맨드라인에서 git 명령어로 작업할 때 이 작업이 가장 까다롭다. 이 작업을 능숙하게 하고싶어서 이걸 열심히 정리하고 있는 이유다! 우엥ㅠ
 
6. GitHub저장소에 수정사항 반영하기
    - GitHub용 SSH키를 만들고, 키를 GitHub에 등록해야 한다.
    - 하지만 GitHub Desktop에서는 자체적 인증을 통해 수정사항을 원격 저장소에 반영하기 때문에 이 과정을 생략해도 좋다.
    - GitHub Desktop에서는 이 모든 사항을 Push 하면 된다.
        
        <img width="626" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6 46 37" src="https://github.com/minkimNV/SelfLearning/assets/150657776/0a08478d-fe91-45e0-8068-e726a4cf0a82">

    - Git CLI로는 아래와 같은 명령어를 사용한다.
    
    ```bash
    git remote add origin git@github.com:minkimNV/GitTutorial.git
    ```
