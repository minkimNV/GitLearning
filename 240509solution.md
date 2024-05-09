# git은 할 때마다 새롭다..



### 1.
---
<img width="880" alt="스크린샷 2024-05-09 오후 8 57 56" src="https://github.com/minkimNV/GitLearning/assets/150657776/a7aa59a4-4ec2-4773-ba4e-ae961c9742ff">
---

- ```git init```

- ```git remote -v```
> origin	git@github.com:minkimNV/CodingStudy.git (fetch) <br>
> origin	git@github.com:minkimNV/CodingStudy.git (push) <br>

- ```git add .```

- ```git commit -m 'commit for movement'```

- ```git push origin master```
> error: src refspec master does not match any <br>
> error: 레퍼런스를 'github.com:minkimNV/CodingStudy.git'에 푸시하는데 실패했습니다 <br>
<br>

**여기서 문제라고 생각한 것:** <br>
**branch가 main인데 master로 push해서 그렇다고 생각했음. 그래서 바로 다시 그 부분 정정했지만 또 push 실패했다.** <br><br>



### 2.
---
<img width="887" alt="스크린샷 2024-05-09 오후 9 00 02" src="https://github.com/minkimNV/GitLearning/assets/150657776/6d20a772-4511-4564-8194-f67ebe939c77">
---

- ```git status```
> 현재 브랜치 main <br>
> 커밋할 사항 없음, 작업 폴더 깨끗함<br>

- ```git branch```
> * main <br>

- ```git push origin main```
> git@github.com: Permission denied (publickey).
> fatal: 리모트 저장소에서 읽을 수 없습니다 <br>
> 올바른 접근 권한이 있는지, 그리고 저장소가 있는지 확인하십시오. <br>

**브랜치 main이다.** <br>
**그래서 main으로 다시 push하려고 했는데 바로 또 다른 오류가 뜬다.** <br>
**Permission Denied! 익숙한 에러의 냄새가 난다. public key 오류라는 힌트를 얻었으니..** <br>




### 3. 진짜 해결
##### SSH 키 확인

```ls -al ~/.ssh``` : SSH 키 확인. id_rsa, id_rsa.pub 또는 id_ed25519, id_ed25519.pub과 같은 파일들을 찾는다. 키가 있다면 사용 중인 키가 제대로 등록되어 있는지 확인해야 한다. <br>

```cat ~/.ssh/config``` : 깃허브 접속 시 어떤 키 사용하는지 확인. 나는 계정마다 호스트별칭을 사용했는데 git remote 설정 시 호스트별칭을 생략하고 설정했다는 걸 깨달았다. 다시 설정해용! <br>

```git remote -v``` <br>
>> origin	git@github.com:minkimNV/CodingStudy.git (fetch) <br>
>> origin	git@github.com:minkimNV/CodingStudy.git (push) <br>
> 기존 주소는 위와 같다. <br>

```git remote set-url origin git@github.com-naver:minkimNV/CodingStudy.git``` : 호스트 별칭이었던 github.com-naver 사용해서 다시 remote 설정한다. <br>

```git push origin main``` : 브랜치 메인!으로 푸시한다. <br>

앗 그전에 ssh 연결 테스트해서 정상적으로 깃허브 서버에 연결되는지 확인 ```ssh-T git@github.com-naver``` <br>
> Hi minkimNV! You've successfully authenticated, but GitHub does not provide shell access. <br>
<br>

<img width="879" alt="스크린샷 2024-05-09 오후 8 43 19" src="https://github.com/minkimNV/GitLearning/assets/150657776/96d25c84-9f52-4dee-8ed7-8b186a96eba6">
