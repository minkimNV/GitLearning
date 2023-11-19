# Homebrew 설치
<br>
Git을 진작에 제대로 했으면 좋았을텐데 그렇지 못했어서 새롭게 계정을 파봤다. 그런데 맥북에서 Git을 하려니 homebrew 설치하라고 한다. 분명 brew를 사용해왔던 기억이 있는데.. 🤔 

일단 homebrew 설치한다.
<br>
<br>
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
<br>

터미널에서 위와 같은 명령어를 입력한다. Homebrew 설치 웹사이트 ([https://brew.sh](https://brew.sh/)) 참고하면 좋다.
<br>
<br>

```bash
==> Checking for `sudo` access (which may request your password)...
Password:
```
<br>

위와 같은 결과가 뜨면 본인이 설정한 맥 비밀번호를 치면 된다.
<br>
<br>

> Press RETURN/ENTER to continue or any other key to abort:

<br>

프레스 엔터 해주고 나면 설치가 시작된다. 

설치가 끝나고 봐야할 건 **Next Steps** 이다. 친절하게 뭐해야 할 지 알려줌.
<br>
<br>

> ==> /usr/bin/sudo /usr/sbin/chown -R minkim:admin /opt/homebrew
> 
> .
> .
> .
> 
> Warning: /opt/homebrew/bin is not in your PATH.
> Instructions on how to configure your shell for Homebrew
> can be found in the 'Next steps' section below.
> **==> Installation successful!**

<br>
<br>
설치가 완료됐다는 걸 알려주고 바로 Next Step이 나온다
<br>
<br>


> **==> Next steps:**<br>
> <br>
> Run these two commands in your terminal to add Homebrew to your PATH:<br>
> (echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/minkim/.zprofile<br>
> eval "$(/opt/homebrew/bin/brew shellenv)"<br>
> - Run brew help to get started<br>
> - Further documentation:<br>
> [https://docs.brew.sh](https://docs.brew.sh/)<br>

<br>
<br>
환경변수 설정해주는건데 아래와 같이 명령어 입력한다.
<br>
<br>

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/minkim/.zprofile
```

<br>
<br>

```bash
eval "$(/opt/homebrew/bin/brew shellenv)"
```

<br>
<br>
위와 같은 명령어를 입력해주어야 하는 이유는.. 그렇지 않고 `brew` 명령어를 실행해주면 not found 라는 에러가 뜬다. M1 칩에서만 생기는 에러인데 이거 없으려면 환경 변수 설정을 해줘야 함. 하라면 하는게 좋다.
<br>
<br>

```bash
brew --version
```

<br>
<br>
그 다음 설치가 잘 됐는지 확인하기 위해 위 명령어를 입력하면 버전이 딱 뜬다.
<br>
<br>

<img width="649" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-13_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5 34 19" src="https://github.com/minkimNV/SelfLearning/assets/150657776/9d7b9c1f-e22a-4b5a-b6e7-38f27dda2c57">

<br>
<br>
설치 완료.
<br>
<br>
