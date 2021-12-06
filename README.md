# Algorithm

## python 기본문법 정리

### 1. 변수 | 타입 | 기본연산 | 진수

```
#  기본 연산자
print(7/3)  # 소수점 챙기는 나눗셈
print(7//3)  # 소수점 버리는 나눗셈
print(7 % 3)  # mod
print(2 ** 3)  # pow

# 몫 과 나머지
print(divmod(7, 3))  # 튜플로 (2,1) 반환.

# 형 변환
print(type(3.3))  # float 형
print(int(3.3))  # 소수점 버리기 | int형
print(int('10'))  # string to int
print(str(10)) # int to str

# 2,8,16 진수 포멧

print(0b101)  # 십진수로 5

print(0o10)  # 십진수로 8

print(0xF)  # 십진수로 15

# 출력 진수 포멧 정하기
# https://www.acmicpc.net/problem/11816
a = input()
if(a[0] == '0'):
    if(a[0:2] == '0x'):
        print(int(a[2:], 16))
    else:
        print(int(a[1:], 8))

else:
    print(int(a))
```

### 2. 변수선언

```
# variable & type

a, b, c = 10, '20', 30

print(a, b, c)
print(type(a), type(b), type(c))

# Swap

a, c = c, a
print(a, b, c)

# variable => None | del

var1 = 10
del var1
# print(var1) # NameError: name 'var1' is not defined
var1 = None
print(var1)  # None
```

### 3. 변수 입력,출력
```
# input

var1 = input()  # input : 10 | str 형으로 입력됨
print(type(var1))

var1 = int(input())  # input : 10 | int로 형 변환
print(type(var1))


# input 한줄을 받아서, 공백으로 구분하기 하지만 str로 들어감

u, v = input().split()
print(u, v)
print(type(u), type(v))

# input 바로 int형으로 받는 방법.

u, v = map(int, input().split())
print(u, v)
print(type(u), type(v))

# print 마다  \n 을 넣기

a, b, c = map(int, input().split(','))  # input 10,20,30
print(a, b, c, sep='\n')  # output 10\n20\n30

# print 마다  \n 을 넣기

a, b, c = map(int, input().split(','))  # input 10,20,30
print(a, b, c, sep='\n')  # output 10\n20\n30

print(a, end='')  # output 102030
print(b, end='')
print(c, end='\n')

print(a, end=' ')  # output 10 20 30
print(b, end=' ')
print(c, end='')
```

### 4. python - 입력 정리, EOF 까지 | 한줄 그냥 | spilt 이용해서
```
# 문자열 한줄을 그냥 받기
a = input()
print(a)

# 공백을 제외한 알맹쓰만 받기 -> 리스트로 반환됨
a = input().split()
print(a)

# EOF(ctrl+Z) 까지 한줄 한줄 입력받기 (공백 포함 싹다 포함)

# https://www.acmicpc.net/problem/11718
import sys

for line in sys.stdin:
    a = line
    print(a, end='')  # line자체가 enter를 포함학 있다.

# EOF(ctrl+Z) 한번에 입력받기 (공백 포함 싹다 포함)

# https://www.acmicpc.net/problem/11718
import sys
v = sys.stdin.read()
print(v, end='')

# EOF(ctrl+Z) 까지 한줄 한줄 입력받기 (공백 없이 알맹이 문자열만)

import sys

for line in sys.stdin:
    a = line.split()
    print(a)

# EOF(ctrl+Z) 까지 정수 a,b  입력받기

import sys

for line in sys.stdin:
    a, b = map(int, line.split())
    print(a + b)

#  공백 포함 문자열 하나하나 분리하기

a = input()
print(list(a))

#  공백 제거 후 문자열 하나하나 분리하기

a = input().split()
for e in a:
    print(list(e))

#  1234 숫자 입력시 , 1,2,3,4 로 하나씩 끊어 받기 ( 공백 처리 불가능  )

a = list(input())
res = list(map(int, a))

print(res)

#  1234 숫자 입력시 , 1,2,3,4 로 하나씩 끊어 받기 ( 공백 처리 가능 )
ans = []
a = input().split()
for e in a:
    res = list(map(int, e))
    ans.extend(res)

print(ans)

# 뛰어쓰기 처리하기 -> replace('\n','')

import sys

var = sys.stdin.read()
var = (var.replace('\n', '').split(','))
print(sum(list(map(int, var))))

# EOF 까지 한번에 읽어서, 뛰어쓰기는 제거하고 ,로 나눠서 리스트를 반환후 더한값을 출력하기
# https://www.acmicpc.net/problem/10823
import sys

nlist = [int(x) for x in sys.stdin.read().replace('\n', '').split(',')]
print(sum(nlist))
```

### 5.람다식 | map ( 각원소를 2씩 곱할수있다. ) | filter (배열에서 짝수인경우만 뱉기)
```

# 람다식 | map ( 각원소를 2씩 곱할수있다. ) | filter (배열에서 짝수인경우만 퉤)
# (x,y) => x+y
# lamda x,y: x+y


def g(x): return x**2


(a, b, c) = map(g, [1, 2, 3])  # 람다 없이 각 원소 2제곱
print(a, b, c)


(a, b, c) = map(lambda x: x*2, [1, 2, 3])  # 람다로, 각 원소 2곱
print(a, b, c)

res = list(map(lambda x: x*2, [1, 2, 3]))  # 람다로, 각 원소 2곱
print(res)

wannaEven = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
res = list(filter(lambda e: e % 2 == 0, wannaEven))  # filter오브젝트에서 list로 반환하기.
print(res)
```

### 6.bool과 논리
```
if(True and False or not True):
    while(True):
        if(bool('False')):  # 모든 문자열은 참값!!!
            break
```
### 7.리스트 만들기
```
a = [] # 혹은 a = list()
b = list(range(10)) # 0부터 9까지 range 객체 만들어 list로 변환
print(b)

c = list(range(1, 5)) # [1, 2, 3, 4]
print(c)

c = list(range(1, 11, 2)) # [1, 3, 5, 7, 9] # 1부터 10까지 2씩증가 | 11포함 안됨
print(c)

c = list(range(10, 0, -1)) # [10, 9, 8, 7, 6, 5, 4, 3, 2, 1] 이 역시 0은 미 포함.
print(c)

# for문으로 문자열 리스트 -> 정수 리스트 변환 및 합

nlist = [int(x) for x in ['10', '20', '30']]
print(sum(nlist))
```

### 8.enumerate()
```
var = ['a', 'b', 'c']

for i, val in enumerate(var):
print(i, val)
```
### 9.2차원 배열
```
a = [[10, 20], [30, 40], [50, 60]]

for x, y in a:  # 리스트 자체를 받아서 사용
    print(x, y)

for i in a:  # 리스트를 원소를 2번꺼내 사용
    for j in i:
        print(j, end=' ')

for i in range(len(a)):  # 길이만큼 사용
    for j in range(len(a[i])):
        print(a[i][j])

for i, x in enumerate(a):
    for j, y in enumerate(x):
        print(a[i][j])

for i, x in enumerate(a):
    for j, y in enumerate(x):
        print(a[i][j])

for i, x in enumerate(a):
    for j, y in enumerate(x):
        print(y)
```
### 10.반복문으로 2차원 | 배열만들기
```
a = ['x' for i in range(3)]
print(a) # ['x', 'x', 'x']

a = [[0, 0, 0] for i in range(3)]
print(a) # [[0, 0, 0], [0, 0, 0], [0, 0, 0]]

a = [[0 for i in range(3)] for i in range(3)]
print(a) # [[0, 0, 0], [0, 0, 0], [0, 0, 0]]

# for문으로 리스트 완성하기

nlist = [int(x) for x in ['10', '20', '30']]
print(sum(nlist))
```
### 11. 튜플 만들기 (튜플은 읽기 전용 리스트)
```
c = tuple(range(0, 10)) # range to tuple
print(c) # print (0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
print(list(c)) # tuple to list
```
### 12. 시퀀스 활용
- 시퀀스 자료형이란 : 리스트, 튜플, range,string,bytes, bytearray ==> 슬라이싱 등등 가능

### 13. 시퀀스 존재성
```
a = [0, 1, 2, 'a', "hello", True, [0, 'dos', True], (0, 'impact', False)]

print(1 in a) # 참
print(10 in a) # 거짓
print('a' in a) # 참
print(True in a) # 참

print(1 not in a) # 거짓
print(10 not in a) # 참
print('a' not in a) # 거짓
print(True not in a) # 거짓

print('ll' in a[4]) # 참

print('dos' in a[6])  # 참
print('do' in a[6])  # 거짓
print('do' in a[6][1])  # 참

print('impact' in a[7])  # 참
print('act' in a[7])  # 거짓
print('act' in a[7][1])  # 참
```
### 14. 시퀀스 with => len + * del
```
a = [1, 2, 3]
b = [4, 5, 6, 7, 8, 9, 10]
st = 'hello'
print(len(st)) # 5
print(a+b) # [1, 2, 3, 4, 5, 6]
print(a\*2) # [1, 2, 3, 1, 2, 3]
print(a[-1]) # 3 (뒤에서 첫번째)

del a[1] # 1번째 인덱스 삭제
print(a) # [1, 3]
```
### 15. 시퀀스 with => slice [][:]
```
print(b[0:2]) # [4, 5]
print(b[0:]) # [4, 5, 6, 7, 8, 9, 10]
print(b[0:-1]) # [4, 5, 6, 7, 8, 9]
print(b[0:-1:2]) # 2씩 증가하면서 가져오기 [4, 6, 8]

print(b[::2]) # [4, 6, 8, 10] 짝수번 인덱스만 가져오기.

print(b[::-1]) # 뒤 집기 [10, 9, 8, 7, 6, 5, 4]

print(b[1::] + b[0:1:]) # 로테이션 [5, 6, 7, 8, 9, 10, 4]
```
### 16. sum,min,max,sorted
```
var = [1, 2, 3, 4, -1, 100]

print(sum(var))  # 109
print(min(var))  # 01
print(max(var))  # 100
print(sorted(var))  # [-1, 1, 2, 3, 4, 100]
print(sorted(var, reverse=True))  # [100, 4, 3, 2, 1, -1]

var = (1, 2, 3, 4, -1, 100)

print(sum(var))  # 109
print(min(var))  # 01
print(max(var))  # 100
print(sorted(var))  # [-1, 1, 2, 3, 4, 100]

var = "EABCD"
# print(sum(var))  #TypeError: unsupported operand type(s) for +: 'int' and 'str'
print(min(var))  # A
print(max(var))  # E
print(sorted(var))  # ['A', 'B', 'C', 'D', 'E']
```
### 17. 리스트 append sort reverse index insert remove pop count extend
```
a = [50, 20, 3, 4, 5]
a.append(6)
print(a)  # [50, 20, 3, 4, 5, 6]

a.extend([7, 8])
print(a)  # [50, 20, 3, 4, 5, 6, 7, 8]

a.sort()
print(a)  # [3, 4, 5, 6, 7, 8, 20, 50]

a.sort(reverse=True)
print(a)  # [50, 20, 8, 7, 6, 5, 4, 3]

a.reverse()
print(a)  # [3, 4, 5, 6, 7, 8, 20, 50]

idx = a.index(20)  # 현재 20의 위치는 6번째.
print(idx)  # 6

a.insert(idx, 21)  # 20위치가 하나 밀리고, 21이 들어감
print(a)  # [3, 4, 5, 6, 7, 8, 21, 20, 50]

a.remove(21)  # 21 찾아서 제거
print(a)  # [3, 4, 5, 6, 7, 8, 20, 50]

a.pop()
a.pop()
print(a)  # [3, 4, 5, 6, 7, 8]

print([3, 3, 3, 2, 2, 1].count(3))  # 3
```
### 18. 딕셔너리 사용(obj)
```
x = {'base': 1, 'dos': 20}
print(x['base'])

# 피보나치 + dp for문 | dp 재귀

d = {}


def dp(n):
    if(n <= 1):
        return n
    if((n) in d):
        return d[(n)]
    d[n] = dp(n-1)+dp(n-2)
    return d[n]


var = int(input())
d[0] = 0
d[1] = 1
for i in range(2, var+1):
    d[i] = d[i-1] + d[i-2]
print(dp(var))
```