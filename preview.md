## Backlog 원숭이

### commit 변경하기
#### 1. 이전에 작성한 commit 수정하기

`--amend`을 지정하여 commit을 수행하면, 같은 브랜치 상에서 이전에 commit했던 내용에 새로운 내용을 추가하거나 설명을 수정할 수 있다.

* 누락된 파일을 새로 추가하거나 기존의 파일을 업데이트 해야할 때
* 이전 commit의 설명을 변경하고 싶을 때


#### 2. 이전에 작성한 commit 지우기

`revert`을 이용하면 특정commit의 내용을 삭제할 수 있다.
`rebase-i`나 `reset`을 통해 commit을 삭제할 수도 있지만, 해당 commit이 이미 공개된 상태인 경우에는 삭제작업이 어려움.
이 때는 `revert`을 이용해서 특정 commit의 내용을 지우는 새로은 commit을 만들 수 있다.

> `revert`을 사용하여 commit B의 내용을 뒤집어 원래의 commit A의 상태로 돌아갈 수 있는 새로운 commit B'을 만들 수 있다.
* 이전에 작성한 commit을 안전하게 지우고 싶을 때


#### 3. commit을 버리고 특정 버전으로 다시 되돌아가기

`reset`을 이용하면 더이상 필요없어진 commit을 버릴 수 있다. 명령어 실행 시 어떤 모드로 실행할 지 지정하여 `HEAD`위치와 인덱스, 작업트리내용을 함께 되돌릴지 여부를 선택할 수 있다.
* 모드: `mixed`지정, soft와 hard 중 선택 가능
* commit만 되돌리고 싶을 때: `soft`
* 변경한 인덱스의 상태를 원래대로 되돌리고 싶을 때: `mixed`
* 최근의 commit을 완전히 버리고 이전의 상태로 되돌리고 싶을 때: `hard`


#### 4. 다른 branch로부터 특적 commit을 가져와서 내 branch에 넣기

`cheery-pick`을 이용하면 다른 branch에서 지정한 commit을 복사하여 현재 branch로 가져올 수 있다.

* 특정 branch에 잘못 추가한 commit을 올바른 branch로 옮기려고 할 때
* 다른 branch의 commit을 현재 branch에도 추가하고 싶을 때


#### 5. commit 이력 편집하기

`rebase`에 `i`옵션을 지정하면 commit을 다시 쓰거나 다른 commit과 바꿔 넣을 수 있으며 특정 위치의 commit을 삭제하거나 여러 commit을 하나로 통합하는 작업을 할 수 있다.

* `push`하기 전에 이전의 commit내용을 정리하고자 할 때
* 그룹으로 묶을 수 있는 commit들을 알기 쉽게 하나로 통합하려고 할 때
* 이전commit에 누락된 파일들을 나중에 추가하고자 할 때