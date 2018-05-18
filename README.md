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

### 3. Crawling을 위한 BeautifulSoup
#### (1) Crawling 정의
- Web상에 존재하는 Contents를 수집하는 작업 (프로그래밍으로 자동화 가능)
  - HTML 페이지를 가져와서, HTML/CSS등을 파싱하고, 필요한 데이터만 추출하는 기법
  - Open API(Rest API)를 제공하는 서비스에 Open API를 호출해서, 받은 데이터 중 필요한 데이터만 추출하는 기법
  - Selenium등 브라우저를 프로그래밍으로 조작해서, 필요한 데이터만 추출하는 기법
  
#### (2) BeautifulSoup 라이브러리
- HTML의 태그를 파싱해서 필요한 데이터만 추출하는 함수를 제공하는 라이브러리
- 사용하기 위해서는 콘솔창 혹은 터미널 창에 # pip install bs4를 입력하여 설치해야 한다. 

### (3) requests

''''javascript
 1) reqeusts 라이브러리를 활용한 HTML 페이지 요청 
# 1-1) res 객체에 HTML 데이터가 저장되고, res.content로 데이터를 추출할 수 있음
res = requests.get('http://v.media.daum.net/v/20170615203441266')
 
# print(res.content)
# 2) HTML 페이지 파싱 BeautifulSoup(HTML데이터, 파싱방법)
# 2-1) BeautifulSoup 파싱방법
soup = BeautifulSoup(res.content, 'html.parser')
 
# 3) 필요한 데이터 검색
title = soup.find('title')
title2 = soup.find_all('title')
 
# 4) 필요한 데이터 추출
print(title.get_text())
print(title2[0].get_text())
