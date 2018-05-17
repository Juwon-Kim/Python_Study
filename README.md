# Python 정리

## 1. 파이썬의 변수와 객체

````javascript
x = 100
y = 100

print(id(x))
print(id(y))

** 문제 : x와 y의 주소값은 같은 값일까? **
                                                                          => 답 : No


x = 10000
y = 10000
print(id(x))
print(id(y))

** 문제 : x와 y의 주소값은 같은 값일까? **
                                                                          => 답 : Yes
sol ) 자주 사용되는 숫자인 256까지는 주소값이 같게 설정되지만 그 이상부터는 숫자의 값이 같더라도
      다른 주소값을 가지게 된다.
                                                                          
                                                                          
````

## 2. 문자열 자료형

### (1) 문자열 저장방식


````javascript

- 문자열은 리스트 형태로 저장되기 때문에 각 문자별로 인덱스번호가 있다. 

** 문제 : Pithon이라는 문자열을 Python으로 바꾸려면 몇 번의 방식이 가능할까?

[방식 1]
>>> a = "Pithon"
>>> a[1]
'i'
>>> a[1] = 'y'


[방식 2]
>>> a = "Pithon"
>>> a[:1]
'P'
>>> a[2:]
'thon'
>>> a[:1] + 'y' + a[2:]
'Python'

                                                                                    => 답 : 2
````

### (2) 문자열 Formatting
````javascript
>>> print("I eat %d apples" % 3)            #문자열포맷팅 ( 숫자 삽입 )
>>> print("I eat %s apples" % "five")       #문자열포맷팅 ( 문자열 삽입 )
>>> print( "I ate %d apples. so I was sick for %s days" %( 3, "five") )         #문자열포맷팅 ( 숫자 + 문자열 삽입 )

%s	문자열 (String)
%c	문자 1개(character)
%d	정수 (Integer)
%f	부동소수 (floating-point)
%o	8진수
%x	16진수
%%	Literal % (문자 % 자체)

1) Formatting연산자(%)와 Percent(%)를 같이 쓸 때는 %%로 표현한다.
>>> print("Error is %d%%" % 98)
'Error is 98%'


2) Formatting을 이용한 정렬과 공백 그리고 소수점 표현

>>> "%10s" % "hi"       #( hi를 오른쪽으로 정렬하기 )
'         hi'

>>> "%-10s" % "hi"      #( hi를 왼쪽으로 정렬하기 )
'hi       jane'

>>> "%0.4f" % 3.42134234    #( 3.4213으로 소수점 4번째까지 표현하기 )



````

### (3) foramt함수

````javascript

print( "I eat {0} apples. so I was sick for {1} days".format(10,'friday') )   #인덱스로 값 삽입
print ( " I eat {number} apples. so I was sick for {day} days".format(number=10, day=3) )     # 변수명으로 값 삽입
print( " I eat {0} apples. so I was sick for {day} days".format(10, day= 1000) )    #인덱스+변수명으로 값 삽입
print( " {0:<10}".format("hi") )    # 왼쪽 정렬
print( " {0:>10}".format("hi") )    # 오른쪽 정렬
print( " {0:^10}".format("hi") )    # 가운데 정렬

````

### (4) 문자열 관련 함수들

````javascript

1) count함수

>>> a = "kimjuwon"
>>> a.count("j")
1

2) find함수 ( 해당 문자열이 있으면 인덱스를 반환하고 없으면 -1을 반환한다 )

>>> a = "kimjuwon"
>>> a.find("u")
4


3) index함수 ( 위와 마찬가지지만 없으면 -1을 반환하는 것이 아닌 오류가 발생한다. ) 

>>> a = "Life is too short"
>>> a.index('t')
8
>>> a.index('k')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: substring not found

4) join함수

>>> a=","
>>> a.join("abcd")
'a,b,c,d'

5) upper(대문자로) / lower(소문자로) 함수

>>> a = 'hi'
>>> a.upper()
'HI'

6) strip / lstrip / rstrip 함수 ( 공백지우기 )

>>> a = " hi "
>>> a.lstript()       # 왼쪽공백지우기
'hi  '


7) replace 함수

>>> a = "Life is too short"
>>> a.replcae("Life" , "Your leg")
'Your leg is too short'


````

