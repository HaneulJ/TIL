## 1/18 수업(2)_PYTHON

#### [ 에러 ]

> 구문적으로 잘못된 것이 인식되면 에러를 발생시키고 처리 종료



#### [예외]

> 프로그램에 구문적인 에러는 없지만 실행하는 동안 발생할 수 있는 잘못된 상황

1. 발생한 예외를 처리하는 코드가 준비되어 있는지 확인하고 준비되어 있는 예외처리 코드를 실행한다.
2. 예외처리 코드가 준비된 상황이 아니면 에러를 발생시키고 처리를 종료한다.



#### [예외 처리 구문]

**`try ~ except(s)... ~ else ~ finally`**

```
try;
	예외가 발생할 가능성이 있는 블록
		:
except[처리하려는 예외명]:
	예외처리 코드 블록
else:
	예외가 발생하지 않았을 때 수행되는 코드 블록
finally:
	예외 발생 여부와 관계없이 수행되는 코드 블럭	
```







### 1. 예외처리

#### 예외

> 프로그램 코드는 이상이 없으나 실행 중에 불가피하게 발생하는 문제

* 에러 발생 직후 프로그램 종료되어 이후 명령 무시
* Value error: exception이 가지고 있는 모든 에러를 표시

```
try:
	실행할 명령
except 예외 as 변수:
	오류 처리문
else:
	예외가 발생하지 않을 때의 처리
```

* `try: except:`까지만 사용하는 것도 가능
* 상황자체를 해결X, 예외 인식/처리기회 제공
* 종류
  * NameError: 명칭 발견x, 초기화하지 않은 변수를 사용할 때
  * ValueError: 타입은 맞지만 값의 형식이 잘못됌
  * ZeroDivisionError: 0으로 나눔
  * IndexError: 첨자가 범위를 벗어남
  * TypeError: 타입이 다름
* 두 개 이상 괄호로 묶어 `except`블록에서 동시에 받기 가능

```
except (ValueError, IndexError):
	print("점수의 형식이나 첨자가 잘못되었습니다.")
```



### 2. 자원 정리

#### finally 블록

> 예외 발생 여부와 무관하게 반드시 실행해야 할 명령 지정



#### raise 명령

> 고의적으로 예외 발생

* 작업을 위한 선결조건이 맞지 않거나 문제 발생 경우 호출원으로 사용



#### assert 문장

> 프로그램의 현재 상태가 맞는지 확인

* `assert 조건, 메세지` 





#### file input&output

```
>>> f = open("파일이름.형식", "모드", encoding="UTF-8")

# wt(write text): 텍스트를 출력할 목적으로 파일을 열어라
# rt(read text mode): 텍스트를 읽을 목적으로~
# encoding="UTF-8": 캐릭터(문자)셋을 UTF-8로 하라
# encoding을 안줄 경우 자동으로 cp949로 > window10에서 안읽힘

>>> print(f, type(f))
>>> f.write("""~~~내용""")
# f.read() 하면 파일을 읽겟다~

>>> f.close()
# 파일이 존재하고 열려있을 때 close될 수 있도록 확인해야 함
>>> if f:
		f.close()
```

* 문자셋(characterset): 문자마다 부여한 코드값들을 모아 놓은 것, 각 문자셋마다 고유 명칭 있음
* 기억할 만한 문자셋 명칭
  * `ansi`(euc-kr,ksc5601, cp949): 영문 1바이트(ASCII값), 한글 2바이트
  * `utf-16`: unicode, 모든 나라의 언어에 대한 코드 값 2바이트로 통일 
  * `utf-8`: utf-16 보안, 1~4바이트로 표현



```
>>> help(open)

'r'       open for reading (default)
'w'       open for writing, truncating the file first
'x'       create a new file and open it for writing
'a'       open for writing, appending to the end of the file if it exists
'b'       binary mode
't'       text mode (default)
'+'       open a disk file for updating (reading and writing)
'U'       universal newline mode (deprecated)
```



* `f.readline()`: 행 단위로 읽기

* `f.readlines()`: 모든 행을 읽기

```
>>> rows = f.readlines()  # 모든 행을 읽어서 리스트로 리턴
>>> for row in rows:
    	print(row, end = '')
```

* **중요 예제**

```
>>> f = open("live.txt", "rt", encoding="UTF-8")
>>> for line in f:       
    	print(line, end = '')
>>> f.close()
# _io.TextIOWrapper 객체도 리터러블함
```



* `at`: 기존 내용에서 추가 할 때(append text)

```
>>> f = open("live.txt", "at", encoding="UTF-8")
>>> f.write("\n\n[추가]푸쉬킨 형님의 말씀이었습니다.")
>>> f.close()
```



* with as 구문: `close`처리 필요X

```
>>> with open("live.txt", "rt", encoding="UTF-8") as f:
   		text = f.read()
>>> print(text)

# close 안해도 됌! 자동으로 닫힘
```

