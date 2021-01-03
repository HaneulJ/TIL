# Git TIL (1/3)

### 복습하기

#### 1. branch 만들기

``` 
$ mkdir tutorial
$ cd tutorial
$ git init
```

```
$ touch myfile.txt
$ git add myfile.txt
$ git commit -m "first commit"
```

```
$ git branch issue1
```

#### 2. branch 전환하기

```
$ git checkout issue1
```

```
$ git add myfile.txt
$ git commit -m "add review alone"
```

#### 3. branch 병합하기

```
$ git checkout master
```

```
$ git merge issue1
```

#### 4. branch 삭제하기

```
$ git branch -d issue1
$ git branch
```

#### 5. 동시에 여러 작업하기

```
$ git branch issue2
$ git branch issue3
$ git checkout issue2
```

```
$ git add myfile.txt
$ git commit -m "Add review 2"
```

```
$ git checkout issue3
$ git add myfile.txt
$ git commit -m "pull today review"
```

#### 6. 병합할 때 발생하는 충돌 해결하기

```
$ git checkout master
$ git merge issue2
```

```
$ git merge issue3
```

```
$ git add myfile.txt
$ git commit -m "issue3 branch merge"
```



### TIL

#### 7. rebase로 병합하기

> 'issue3' 브랜치를 병합할 때 `rebase`를 먼저 실행한 후 병합을 시도하면 그 이력을 하나의 줄기로 만들 수 있다.
>
> 이전의 튜토리얼에서 마지막으로 진행했던 병합명령을 먼저 취소한다.

```
$ git reset --hard HEAD~
```

```
$ git checkout issue3
$ git rebase master
```

* `merge`때와 같이 myfile.txt 파일 내용에 충돌이 있기 때문에 그 부분을 이전의 튜토리얼에서와 동일하게 처리한다. 충돌난 파일 내용을 적절히 변경

> `rebase`의 경우 충돌 부분을 수정한 후에는 `commit`이 아니라 `rebase`명령에 **`--continue`**옵션을 지정하여 실행해야 한다.

```
$ git add myfile.txt
$ git rebase --continue
```

* 만약 `rebase`자체를 취소하려면 **`--abort`**옵션을 지정하면 된다.



branch의 변경사항을 모두 병합한다.

```
$ git checkout master
$ git merge issue3
```

