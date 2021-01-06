## 1/6 수업

**순서도작성.pdf 확인**

https://www.w3schools.com/



### 제어문

> 프로그램의 수행 흐름을 제어한다.

* 조건 제어문: IF(문), elif(절), else(절) >> 같이 사용
* 반복 제어문: for, while >> 따로 사용
  * for: 몇 번 반복할 지 예측 가능할 때(횟수 적용)
  * while: 반복 횟수가 예측 불가능할 때, 어떤 반복문이 참이 될 때까지 반복~

* 분기 제어문: break, continue, 흐름을 바꾼다
  * break: 반복문을 강제 종료
  * continue: 다음 반복문으로 넘어가는 제어문





### 반복문

#### for문

> **for 변수 in 데이터값집합:**
>
> ​	**반복처리 할 수행문장의 블럭**
>
> #데이터값집합: 반복횟수의 기준

```
>>> for d in [10, 20, 30] :
		print(d)

# 화면에 10, 20, 30의 결과값이 세로로 표시
# 한줄로 표시하려면 print(d, end=" ")
# end=" "는 개행 처리
```

```
>>> for d in [1,2,3,4,5,6,7,8,9]
		print(3*d)
		
# data값 집합이 가지고 있는 데이터 갯수만큼 반복
```

```
# 범위를 나타내는 함수: range(시작값, 끝값+1, 증가값)
>>> for d in range(1, 20, 1) # 1부터 19까지 1씩 올라가면서 반복
		print(3*d)
```

```
range(10)		 # range(끝값+1), 자동으로 시작값=0, 단계=1
range(1,10) 	 # 1~9 범위
range(1,10,2) 	 # 1~9 범위, 2씩 증가
range(10,1,-1) 	 # 10,9,8,7,6,5,4,3,2
range(10,101,10) # 10,20,30,40,50,60,70,80,90,100
```



* i값 코드 내부 사용

```
>>> for i in range(0,3,1):
		print("%d: 안녕하세요? for문을 공부중입니다. ^^" %i)
0: 안녕하세요? for문을 공부중입니다. ^^
1: 안녕하세요? for문을 공부중입니다. ^^
2: 안녕하세요? for문을 공부중입니다. ^^

# i변수의 값을 d자리에 for문에 맞게 출력하라
```

```
>>> for i in range(2,-1,-1):
		print("%d: 안녕하세요? for문을 공부중입니다. ^^" %i)
2: 안녕하세요? for문을 공부중입니다. ^^
1: 안녕하세요? for문을 공부중입니다. ^^
0: 안녕하세요? for문을 공부중입니다. ^^
```

* 제어 변수의 활용: 루프의 반복횟수와 끝낼 시점을 결정
* **%연산자**: 배수를 판별 = **%d**



* 예시

```
>>> startNum = int(input("시작 숫자 : "))
>>> endNum = int(input("종료 숫자 : "))
>>> incNum = int(input("증가치 숫자 : "))

>>> for num in range(startNum, endNum+1, incNum) :
    	print(num, end=" ")

# 증가치 숫자가 양수 일때만 정상적으로 실행
```

```
>>> if startNum > endNum and incNum < 0 :
    	endNum -= 1
	else :
   		endNum += 1
>>> for num in range(startNum, endNum, incNum) :
    	print(num, end=" ")
```





#### while문

>**while 조건식:**
>
>​	**반복하려는 수행문장블럭**
>
>#조건식이 '참'인 동안, 만족되는 동안 반복해라	

* 조건이 만족하는 동안 명령 계속 실행
* 루프(Loop): 반복적으로 처리
* 반복문은 코드변경이 쉬움(조건식이나 출력문 변경을 통해 수정)



> **while True: **
>
> ​	**반복하려는 수행문장블럭**
>
> #무한루프, break사용 가능

```
>>> while True:
		반복하려는 수행문장 블럭
	if 조건식:
		break
```

```
>>> score = [92, 86, 68, 120, 56]
>>> for s in score:
		if s < 0 or s > 100:
			break
		print(s)
>>> print("성적 처리 끝")
92
86
68
성적 처리 끝
```

```
>>> score = [92, 86, 68, 120, 56]
>>> for s in score:
		if s < 0 or s > 100:
			continue
		print(s)
>>> print("성적 처리 끝")
92
86
68
56
성적 처리 끝
```



##### * 이중 루프 (들여쓰기 주의!)

```
>>> for dan in range(2, 10):
		print(dan, "단")
		for hang in range(2,10):
			print(dan, "*", hang, "=", dan*hang)
		print()
2단
2 * 2 = 4
2 * 3 = 6
2 * 4 = 8
2 * 5 = 10
2 * 6 = 12
2 * 7 = 14
2 * 8 = 16
2 * 9 = 18

3단
...
# 9단까지 출력, 64번 반복
```

```
>>> dan = 2
>>> while dan <= 9:
		hang = 2
		print(dan, "단")
		while hang <= 9:
			print(dan, "*", hang, "=", dan*hang)
			hang += 1
		dan += 1
		print()
# while문보다 for문이 더 간단
```

