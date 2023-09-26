# 함수
- 함수를 왜 사용할까요 ?
  - 분해
    - 기능을 분해하고 재사용 가능하게 만듬
  
    ```python
    numbers = [1,2,3]
    def average(numbers) :
        return sum(numbers) / len(numbers)
    print(average(numbers)) # 2.0

    ```
  - 추상화
    - 복잡한 내용을  모르더라도 사용할 수 있도록 재사용성 가독성,생산성
      - 내부 구조를 변경할게 아니라면 몰라도 무방
        - 그것이 함수의 장점이자 프로그래밍의 매력


### 함수의 종류
- 크게 3가지로 분류
  - 내장 함수
    - 파이썬에 기본적으로 포함된 함수
  - 외장 함수
    -  import 문을 통해 사용하며, 외부 라이브러리에서 제공하는 함수
  - 사용자 정의 함수
    - 직접 사용자가 만드는 함수

### 함수의 정의
- 함수
  - 특정한 기능을 하는 코드의 조각(묶음)
  - 특정 코드를 매번 다시 작성하지 않고, 필요시에만 호출하여 간편히 사용

- 함수 기본 구조
  - 선언과 호출
  - 입력
  - 문서화
  - 범위
  - 결과값

### 선언과 호출
- 함수의 선언은 def 키워드를 활용함
- 들여쓰기를 통해 Function body(실행될 코드 블록)를 작성
- 동작 후 return을 통해 결과값 전달
- 함수는 함수명()으로 호출하여 사용
  - parameter가 있는 경우, 함수명(값1,값2,... )으로 호출
   ```python
   def foo() : 
    return True

    def add(x,y) :
        return x + y
  ```

### 함수의 결과값
- 값에 따른 함수의 종류
  - Void function
    - 명시적인 return 값이 없는 경우, None을 반환하고 종료

- Value returning function
  - 함수 실행 후, return문을 통해 값 반환
  - return을 하게되면,값 반환 후 함수가 바로 종료

```python
a = print('hello world')
b = float('3.14')

print(a) # None
print(b) # 3.14
```

### 주의 - print vs return
- print 함수와 return의 차이점
  - print를 사용하면 호출될 때마다 값이 출력됨(주로 테스트를 위해 사용)
  - 데이터 처리를 위해서는 return 사용

- 튜플을 활용하여 두개 이상의 값 반환
  - 반환 값으로 튜플 사용(or 리스트, 컨테이너)
```python
def test(x,y) :
    return x - y, x * y
```

- return X -> None
- return O -> 반환

### 함수의 입력
- parameter : 함수를 정의할 때, 함수 내부에서 사용되는 변수
- Argument : 함수르 호출 할 때, 넣어주는 값
  - 함

```python
def function(ham) : # ham : parameter
    return ham

function('spam') # argument : 'spam'
```
- Positional Arguments
  - 기본적으로 함수 호출 시 Argument는 위치에 따라 함수에 전달됨
```python
def add(x,y) :
    return x + y
```
- Keyword Argument
  - 직접 변수의 이름으로 특정 Argument를 전달할 수 있음
  - Keyword Argument 다음에 Positional Argument 활용 불가
  ```python
  add(x = 2, y = 5)
  add(2, y = 5)
  add(x = 2, 5) -> Error
  ```


- Default Arguments Values
  - 기본값을 지정하여 함수 호출 시 Argument 값을 설정하지 않도록 함
    - 정의된 것 보다 더 적은 개수의 Argument 들로 호출될 수 있음
    ```python
    def add(x, y = 0): 
        return x + y
    ```

## Python의 범위 (Scope)
- 함수 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분

- Scope
  - global scope : 코드 어디에서든 참조할 수 있는 공간
  - local scope : 함수가 만든 scope. 함수 내부에서만 참조 가능
- vairalble
  - global vairalble : global vairalble에 정의된 변수
  - local variable : local variable에 정의된 변수

## 변수 수명 주기(Lifecycle)
- 변수는 각자의 수명주기가 존재
  - built - in scope
    - 파이썬이 실행된 이후부터 영원히 유지
  - global scope
    - 모듈이 호출된 시점 이후 부터 인터프리터가 끝날 때까지 유지
  - local scope
    - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지
    - 
### Name space
- 이름을 기억하는 공간
1. built - in Name space : 내장함수(ex : print(),len()) 
2. global Name space : .py 파일 실행할 때 생성
3. enclosing Name space : 함수 내부에서 생성
4. local Name space : 함수 내부안의 함수 내부에서 생성

- 크기순서 4 < 3 < 2 < 1 -> 같은 값 찾을 때 작은 순서대로 찾음

### 이름 검색 규칙
- 파이썬에서 사용되는 이름(식별자)들은 이름공간에 저장되어 있음
- 아래와 같은 순서로 이름을 찾아나가며, LEGB Rule이라고 부름
  - Local scope : 지역 범위
  - Enclose scope : 지역 범위 한 단계 위 범위
  - Global scope : 최상단에 위치한 범위
  - Built-in scope : 모든 것을 답고 있는 범위(정의하지 않고 사용할 수 있는 모든 것)
    - ex : print()
  - **함수 내에서는 바깥 Scope의 볌수에 접근 가능하나 수정은 할 수 없음** 

## 함수의 범위
### global 문
- 현재 코드 블록 전체에 적용되며, 나열된 식별자가 global variable임을 나타냄
  - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음
  - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등을 정의되지 않아야 함
### nonlocal 문
- global을 제외하고 가장 가까운(둘러싸고 있는)scope 변수를 연결하도록 함
  - nonlocal에 나열된 같은 코드 블록에서 nonlocal 앞에 등장할 수 없음
  - nonlocal에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등을 정의되지 않아야 함
  - global과는 달리 이미 존재하는 이름과의 연결만 가능
```python
# global 사용 예시 1
x = 1

def func1():
    x = 2
    def func2():
        global x # global의 x 사용
        x = 3 # global x 변경
        print(x)
    
    func2()
    print(x)

func1()
print(x)

'
3
2
3
'

# global 사용 예시 2
def func1():
  global out 
  out = 3 # 글로벌에 변수생성후 3대입

func1()
print(out) # 3
# nonlocal 사용 예시

x = 1

def func1():
    x = 2
    def func2():
        nonlocal x # 나를 감싼 함수의 x 사용
        x = 3 # func1의 x 변경
        print(x)
    
    func2()
    print(x)

func1()
print(x)

'
3
3
1
'
# 에러 예시

def func():
    a = 20
    print('local', a) # local 20

func()
print('global', a) #Error : name 'a' is not defined
```