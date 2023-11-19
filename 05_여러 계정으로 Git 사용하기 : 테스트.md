# [Git] 여러 계정으로 Git 사용하기 : 부계정테스트

본계정은 아직 안된다 ㅠ 그래도 부계정 계속 안됐는데 되는거 확인해보려고

```bash
cd ~/Documents/Github/tomoo56/

mkdir gitTutorial

cd git Tutorial

git init
```

GitHub에서도 레포지토리를 만들어주고 시작한다.

```bash
echo "#git tutorial" > README.md

git add README.md

git commit -m "first commit test"

git remote add origin git@github.com-naver:minkimNV/gitTutorial.git

git push -u origin main
```

`git remote add origin git@github.com-naver:minkimNV/gitTutorial.git` 은 해당 폴더에서 한 번만 실행해주면 된다. 

<img width="532" alt="%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-14_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_12 52 44" src="https://github.com/minkimNV/SelfLearning/assets/150657776/daaa17f8-4490-4835-9a37-899534753cf4">

성공 ㅠ

---

본 계정은 왜 안되는지 모를 일이당.
