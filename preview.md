## Backlog 원숭이

### commit 변경하기

#### 1. 이전에 작성한 commit 수정하기

`--amend`을 지정하여 commit을 수행하면, 같은 브랜치 상에서 이전에 commit했던 내용에 새로운 내용을 추가하거나 설명을 수정할 수 있다.

* 누락된 파일을 새로 추가하거나 기존의 파일을 업데이트 해야할 때
* 이전 commit의 설명을 변경하고 싶을 때



* 이력 확인하기

```
$ git log
```

* sample.txt 파일을 열고 commit설명 추가하기

```
$ touch sample.txt
$ git add sample.txt
$ git commit --amend
```



```
$ git log
```







#### 2. 이전에 작성한 commit 지우기

`revert`을 이용하면 특정commit의 내용을 삭제할 수 있다.

`rebase-i`나 `reset`을 통해 commit을 삭제할 수도 있지만, 해당 commit이 이미 공개된 상태인 경우에는 삭제작업이 어려움.

이 때는 `revert`을 이용해서 특정 commit의 내용을 지우는 새로은 commit을 만들 수 있다.

> revert`을 사용하여 commit B의 내용을 뒤집어 원래의 commit A의 상태로 돌아갈 수 있는 새로운 commit B'을 만들 수 있다.

* 이전에 작성한 commit을 안전하게 지우고 싶을 때



* 이력 확인하기

```
$ git log
```

* sample.txt파일을 열어 내용 확인

```
$ git pull origin master
```

* `revert`을 사용해 **pull의 설명 추가**하는 commit을 취소

```
$ git revert HEAD
```

* sample.txt을 열어 pull의 설명이 지워졌는지 확인

```
$ git log
```





#### 3. commit을 버리고 특정 버전으로 다시 되돌아가기

`reset`을 이용하면 더이상 필요없어진 commit을 버릴 수 있다. 명령어 실행 시 어떤 모드로 실행할 지 지정하여 `HEAD`위치와 인덱스, 작업트리내용을 함께 되돌릴지 여부를 선택할 수 있다.

```
$ git reset --hard HEAD~~
```

* 모드: `mixed`지정, soft와 hard 중 선택 가능

* commit만 되돌리고 싶을 때: `soft`

* 변경한 인덱스의 상태를 원래대로 되돌리고 싶을 때: `mixed`

* 최근의 commit을 완전히 버리고 이전의 상태로 되돌리고 싶을 때: `hard`



> reset전의 commit은 **`ORIG_HEAD`**로 참조할 수 있다.
>
> 실수로 `reset`을 한 경우에는, 	**`ORIG_HEAD`**로 reset하여 reset 실행 전의 상태로 되돌릴 수 있다.

```
$ gir reset --hard ORIG_HEAD
```





#### 4. 다른 branch로부터 특적 commit을 가져와서 내 branch에 넣기

`cheery-pick`을 이용하면 다른 branch에서 지정한 commit을 복사하여 현재 branch로 가져올 수 있다.

```
$ git checkout master
$ git cherry-pick 99daed2
```

* 충돌 발생했을 때 sample.txt 을 열고 충돌부분을 수정한 후 commit

```
$ git add sample.txt
$ git commit
```

​	

* 특정 branch에 잘못 추가한 commit을 올바른 branch로 옮기려고 할 때

* 다른 branch의 commit을 현재 branch에도 추가하고 싶을 때



#### 5. commit 이력 편집하기

`rebase`에 `i`옵션을 지정하면 commit을 다시 쓰거나 다른 commit과 바꿔 넣을 수 있으며 특정 위치의 commit을 삭제하거나 여러 commit을 하나로 통합하는 작업을 할 수 있다.

* `push`하기 전에 이전의 commit내용을 정리하고자 할 때

* 그룹으로 묶을 수 있는 commit들을 알기 쉽게 하나로 통합하려고 할 때

* 이전commit에 누락된 파일들을 나중에 추가하고자 할 때



* 과거의 commit을 통합할 때는 `rebase -i`사용

```
$ git rebase -i HEAD~~
```

> 두번째 줄의 pick문자를 **`squash`**로 변경하고 저장, 종료한다.
>
> > 두개의 commit이 하나의 commit으로 통합



* sample.txt을 열어 commit의 설명부분을 변경한 후 commit--amend 실행하여 변경한 내용을 저장

```
$ git add sample.txt
$ git commit --amend
```

* commit 작업 종료는 --continue옵션을 지정하여 rebase실행

```
$ git rebase --continue
```



* 다른 commit에서 충돌이 발생하면, 충돌부분을 수정한 후 `add`와 `rebase --continue`실행
* 만약 도중에 rebase작업을 중지하고자 하는 경우에는 `rebase`에 `--abort`옵션 지정하여 실행





#### 6. branch상의 commit을 하나로 모아 병합한다.

**`--squash`**

> branch를 병합하면 해당 branch의 commit전체를 통합한 commit이 추가된다.

* topic branch안의 commit을 한꺼번에 모아서 통합 branch에 병합하고자 할 때



* `master`branch로 이동한 후 **`--squash`**옵션을 지정해 merge 실행

```
$ git checkout master
$ git merge --squash issue1
```

* 충돌이 발생, sample.txt을 열어 충돌 부분을 수정한 후 commit

```
$ git add sample.txt
$ git commit
```

