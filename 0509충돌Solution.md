
```git remote set-url origin git@github.com-naver:minkimNV/SmallProjects.git```

```ssh -T git@github.com-naver```
> Hi minkimNV! You've successfully authenticated, but GitHub does not provide shell access. <br>

```git add --all```

```git add .```

```git commit -m 'commit'```
> 현재 브랜치 main <br>
> 커밋할 사항 없음, 작업 폴더 깨끗함 <br>

```git push origin main```
> To github.com-naver:minkimNV/SmallProjects.git <br>
> ! [rejected]        main -> main (fetch first) <br>
> error: 레퍼런스를 'github.com-naver:minkimNV/SmallProjects.git'에 푸시하는데 실패했습니다 <br>
> 힌트: Updates were rejected because the remote contains work that you do not <br>
> 힌트: have locally. This is usually caused by another repository pushing to <br>
> 힌트: the same ref. If you want to integrate the remote changes, use <br>
> 힌트: 'git pull' before pushing again. <br>
> 힌트: See the 'Note about fast-forwards' in 'git push --help' for details.
<br>

---
**"Updates were rejected" 오류 메시지: 원격 저장소에 로컬 저장소에 없는 변경 사항이 있다는 의미.** <br>
**해결하려면 먼저 원격 저장소의 변경 사항을 로컬로 가져와야 한다.** <br>

---
<br>

1. 원격 변경 사항 병합 : 원격 저장소의 변경 사항을 로컬 저장소로 가져와서 병합한다.

```git pull origin main```
> remote: Enumerating objects: 52, done. <br>
> remote: Counting objects: 100% (52/52), done. <br>
> remote: Compressing objects: 100% (48/48), done. <br>
> remote: Total 52 (delta 13), reused 0 (delta 0), pack-reused 0 <br>
> 오브젝트 묶음 푸는 중: 100% (52/52), 6.92 MiB | 2.65 MiB/s, 완료. <br>
> github.com-naver:minkimNV/SmallProjects URL에서 <br>
>  * branch            main       -> FETCH_HEAD <br>
>  * [새로운 브랜치]   main       -> origin/main <br>
> 힌트: You have divergent branches and need to specify how to reconcile them. <br>
> 힌트: You can do so by running one of the following commands sometime before <br>
> 힌트: your next pull: <br>
> 힌트:   git config pull.rebase false  # merge <br>
> 힌트:   git config pull.rebase true   # rebase <br>
> 힌트:   git config pull.ff only       # fast-forward only <br>
> 힌트: You can replace "git config" with "git config --global" to set a default <br>
> 힌트: preference for all repositories. You can also pass --rebase, --no-rebase, <br>
> 힌트: or --ff-only on the command line to override the configured default per <br>
> 힌트: invocation. <br>
> fatal: Need to specify how to reconcile divergent branches. <br>
<br>
<br>

2. 다시 푸시한다.

```git push origin main```
> To github.com-naver:minkimNV/SmallProjects.git <br>
> ! [rejected]        main -> main (non-fast-forward) <br>
> error: 레퍼런스를 'github.com-naver:minkimNV/SmallProjects.git'에 푸시하는데 실패했습니다 <br>
> 힌트: Updates were rejected because the tip of your current branch is behind <br>
> 힌트: its remote counterpart. If you want to integrate the remote changes, <br>
> 힌트: use 'git pull' before pushing again. <br>
> 힌트: See the 'Note about fast-forwards' in 'git push --help' for details. <br>
<br>
<br>

3. 충돌시: git pull --rebase 옵션 사용. 로컬 변경 사항을 원격 변경 사항에 다시 적용하여 깔끔하게 병합 가능.

```git pull --rebase```
> 현재 브랜치에 추적 정보가 없습니다. <br>
> 어떤 브랜치를 대상으로 리베이스할지 지정하십시오. <br>
> 자세한 정보는 git-pull(1) 페이지를 참고하십시오. <br>
>    git pull <리모트> <브랜치> <br>
> 이 브랜치에 대한 추적 정보를 설정하려면 다음과 같이 할 수 있습니다: <br>
>    git branch --set-upstream-to=origin/<브랜치> main <br>
<br>
<br>
4. 브랜치 추적정보 설정

```git branch --set-upstream-to=origin/main main```
> branch 'main' set up to track 'origin/main'. <br>

<br>
<br>
5. 다시 rebase 수행

```git pull --rebase origin main```
> github.com-naver:minkimNV/SmallProjects URL에서 <br>
> * branch            main       -> FETCH_HEAD <br>
> 자동 병합: 0503Satisfaction_PreprocessingPractice.ipynb <br>
> 충돌 (추가/추가): 0503Satisfaction_PreprocessingPractice.ipynb에 병합 충돌 <br>
> error: 다음을 적용할(apply) 수 없습니다: f69ece2... 0509 commit <br>
> 힌트: Resolve all conflicts manually, mark them as resolved with <br>
> 힌트: "git add/rm <conflicted_files>", then run "git rebase --continue". <br>
> 힌트: You can instead skip this commit: run "git rebase --skip". <br>
> 힌트: To abort and get back to the state before "git rebase", run "git rebase --abort". <br>
> Could not apply f69ece2... 0509 commit <br>


---
**0503Satisfaction_PreprocessingPractice.ipynb 파일이 Jupyter Notebook 파일이므로, 충돌 내용을 텍스트 편집기로 직접 해결하기 어려울 수 있다.** <br>
**Jupyter Notebook 파일의 충돌은 코드와 출력 결과가 복잡하게 섞여 있어 수동으로 수정하는 것이 까다롭다.** <br>

---

6. 충돌 수동 해결

´´´pip install nbdime´´´
> ... Successfully installed colorama-0.4.6 gitdb-4.0.11 gitpython-3.1.43 jupyter-server-mathjax-0.2.6 nbdime-4.0.1 smmap-5.0.1 <br>

´´´ nbdime mergetool 0503Satisfaction_PreprocessingPractice.ipynb´´´
> Merging: <br>
> 0503Satisfaction_PreprocessingPractice.ipynb <br>
<br>
<br>
7. 충돌 해결 후 파일 추가 후 다시 push

```git add 0503Satisfaction_PreprocessingPractice.ipynb```
```git rebase --continue```
> [HEAD 분리됨 66da291] 0509 commit <br>
> 6 files changed, 24902 insertions(+) <br>
> create mode 100644 0503CarPriceRedict.ipynb <br>
> create mode 100644 0503ModelingPractice.ipynb <br>
> create mode 100644 0503PreprocessingPractice.ipynb <br>
> create mode 100644 CarPricePredict.ipynb <br>
> create mode 100644 HeartDiseasePredict.ipynb <br>
> Successfully rebased and updated refs/heads/main. <br>

```git push origin main```
> 오브젝트 나열하는 중: 8, 완료. <br>
> 오브젝트 개수 세는 중: 100% (8/8), 완료. <br>
> Delta compression using up to 8 threads <br>
> 오브젝트 압축하는 중: 100% (7/7), 완료. <br>
> 오브젝트 쓰는 중: 100% (7/7), 1.05 MiB | 4.71 MiB/s, 완료. <br>
> Total 7 (delta 1), reused 0 (delta 0), pack-reused 0 <br>
> remote: Resolving deltas: 100% (1/1), completed with 1 local object. <br>
> To github.com-naver:minkimNV/SmallProjects.git <br>
>    d5910ea..66da291  main -> main <br>
