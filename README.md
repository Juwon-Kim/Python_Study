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
