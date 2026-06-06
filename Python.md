**:closed_book:리스트(List)**  
- 여러 개의 값을 순서대로 저장하는 자료형  
- 순서가 의미가 있음→ 인덱싱 가능, 특정 위치의 요소를 가져올 수 있음  
- 변경 가능 (Mutable) → 값 추가, 수정, 삭제 가능  
- 다양한 데이터 저장 가능 → 정수, 문자열, 리스트 등  
  :book: `append(값)`: 리스트 끝에 요소 추가  
  :book: `insert(인덱스, 값)`: 특정 위치에 요소 추가  
  :book: `extend(리스트)`: 여러 개의 요소 추가  
  :book: `del 리스트[인덱스]`: 특정 요소 삭제  
  :book: `remove(값)`: 특정 값을 찾아 삭제  
  :book: `pop(인덱스)`: 특정 위치의 요소를 꺼내면서 삭제  

**:closed_book: 튜플(Tuple)**  
- 한 번 생성하면 변경할 수 없는(Immutable) 자료형  
- 변경 불가능 (Immutable) → 값을 수정하거나 추가, 삭제할 수 없음  
- 연산 속도가 빠름  

**:closed_book: 딕셔너리(Dictionary)**  
- 키(Key)와 값(Value)의 쌍으로 이루어진 자료형  
- Key로 데이터 접근 → 따라서 Key는 유일해야 함  
- Key는 변경 불가능한 자료형만 가능  
- 값은 변경 가능 (Mutable) → 값 추가, 수정, 삭제 가능  
  :book: `del/ .pop()` : 딕셔너리 값 삭제  
  :book: `dict[key값]/ .get(key값)` : 딕셔너리 값 가져오기

**:book:함수(Function)**  
- 함수는 **반복되는 코드나 특정 기능을 하나로 묶어 실행**하는 구조로, **입력(매개변수)을 받아 처리 후 결과값(return)을 반환**  
- 함수 정의 후 호출해서 사용가능  
- **코드 재사용성, 가독성 및 유지보수 용이**  
- 구조  
```
def 함수이름(매개변수):
    수행할 코드
    return 반환값
```

**:book: 지역 변수 (Local Variable)**  
- 함수 내부에서 선언된 변수로, 해당 함수 안에서만 유효  
- 함수가 종료되면 메모리에서 사라짐  
- 다른 함수나 코드에서 사용할 수 없음  

**:book: 전역 변수 (Global Variable)**  
- 함수 외부에서 선언된 변수로, 프로그램 전체에서 사용 가능  
- 모든 함수에서 값을 변경하고 접근 가능

**:book: global 키워드**  
- 함수 내부에서 전역 변수의 값을 변경하고 싶을 때 사용  

**:book: 리스트 데이터 SWAP (교환)**  
- 리스트에서 두 요소의 위치를 바꾸는 방법
- 임시 변수 없이도 쉽게 SWAP이 가능

**:book: id() 함수와 리스트**  
- id() 함수는 객체의 메모리 주소(고유 ID)를 반환하는 함수  
- 리스트는 가변 객체이므로, 같은 리스트를 여러 변수에서 참조 가능  

**:book: 클래스(Class)**  
> 객체(Object)를 만들어내는 설계도로, 데이터(속성)와 기능(메서드)를 하나로 묶어 관리할 수 있습니다.
> 객체 지향 프로그래밍(OOP)의 핵심 개념으로, 코드 재사용성과 확장성을 높여줍니다.

**:pushpin: 1. 클래스 기본 구조**
```
class 클래스이름:
    def __init__(self, 속성1, 속성2):
        self.속성1 = 속성1
        self.속성2 = 속성2

    def 메서드이름(self):
        print(f"{self.속성1}와 {self.속성2}")
```
:white_check_mark: `__init__` → 객체가 생성될 때 자동으로 호출되는 생성자  
:white_check_mark: `self` → 객체 자신을 의미, 속성과 메서드를 접근하기 위해 사용  

**:pushpin: 2. 클래스 예시**
```
class Student:
    def __init__(self, name, age):
        self.name = name  # 속성
        self.age = age

    def introduce(self):  # 메서드
        print(f"저는 {self.name}이고, 나이는 {self.age}살입니다.")

# 객체 생성
student = Student("Alice", 21)
student.introduce()  # 출력: 저는 Alice이고, 나이는 21살입니다.
```
⚠️ 특정 동작,기능에 필요한 여러 메소드(함수)들이 속성(인스턴스변수)들과 함께 담긴 큰 틀  

**:white_check_mark:모듈(Module)** 
모듈(Module)은 여러 개의 함수와 클래스를 하나의 파일로 저장한 것으로 파이썬 파일(.py) 하나가 모듈.  
예를 들어, math.py라는 파일에 수학 관련 함수들을 작성해 두면, 다른 파일에서 이를 불러와 사용할 수 있습니다.  
즉, 모듈을 사용하면 코드의 재사용성이 높아지고, 유지보수가 쉬워집니다.  

**:white_check_mark:상속(Inheritance)**  
상속은 기존의 클래스를 물려받아 새로운 클래스를 만드는 것입니다.  
예를 들어, 동물이라는 부모 클래스를 만들고, 이를 상속받아 강아지, 고양이 클래스를 만들 수 있습니다.  
 부모 클래스의 기능을 그대로 사용할 수 있으며, 필요한 기능을 추가하거나 변경할 수도 있습니다.  
즉, 코드를 중복 없이 효율적으로 작성할 수 있는 객체지향 프로그래밍의 중요한 개념입니다.  
```
# 상속 예시
class Animal:
    def sound(self):
        print("동물이 소리를 낸다.")

class Dog(Animal):  # Animal클래스를 상속받음
    def sound(self):
        print("멍멍!")

dog = Dog()
dog.sound()  # 멍멍!
```

**:white_check_mark:오버라이딩(Overriding)**  
오버라이딩은 부모 클래스에서 정의한 메서드를 자식 클래스에서 재정의(덮어쓰기) 하는 것입니다.  
위 코드 예시처럼 두 클래스가 같은 sound() 메소드를 사용하지만  
자식클래스인 Dog()에서 부모에게 물려받은 sound() 메소드를 덮어쓰기한 형태입니다.  

**:closed_book: 파일 열기 (open)**
```
f = open("경로/파일이름", "모드", encoding="인코딩")

모드	설명
'r'	읽기 모드 (기존 파일 열기)
'w'	쓰기 모드 (기존 내용 삭제 후 새로 작성)
'a'	추가 모드 (파일 끝에 내용 추가)
```

**:closed_book: 파일 닫기 (f.close())**  
- 파일 작업이 끝나면 반드시 닫기 (자원 반환)  
- 파일을 열고 작업 후에는 메모리 누수 방지를 위해 닫아야 함  

**:closed_book: 파일 읽기 방법**  
```
# 한 줄씩 읽기(readline())
line = f.readline()

## 모든 줄 리스트로 읽기(readlines())
lines = f.readlines()
for line in lines:
    print(line)

### 전체 내용 읽기(read())
content = f.read()
```

**:closed_book: 파일에 내용 추가 (a 모드)**  
```
f = open("file.txt", "a", encoding="utf-8")
f.write("추가 내용\n")
f.close()
```

**:closed_book: with문을 활용한 자동 파일 닫기**
```
with open("file.txt", "w", encoding="utf-8") as f:
    f.write("자동으로 닫힘")
```    
- `with` 구문을 사용하면 코드 블록이 끝나면 자동으로 파일을 닫음  
- 예외가 발생해도 자동 닫힘 처리되므로 권장됨  

**:closed_book: 경로 지정**
- 절대 경로
```
# 전체 경로를 지정 (드라이브부터 시작)
C:/user/data/file.txt
```
- 상대 경로
```
# 현재 작업 디렉토리를 기준
./data/file.txt  (현재 위치 기준)
../file.txt      (상위 폴더 기준)
```
- 현재 경로 확인
```
import os
print(os.getcwd())
```

**:closed_book: 예외 처리 (Exception Handling)**  
>프로그램을 실행하는 동안 오류(예외, Exception) 가 발생할 수 있음  
> 예외 처리는 프로그램이 강제 종료되지 않도록 오류를 잡아내는 방법  
- try: 오류가 발생할 가능성이 있는 코드를 작성  
- except: 오류가 발생했을 때 실행할 코드 작성  
- finally: 오류 발생 여부와 관계없이 항상 실행되는 코드 (선택적)  

**:closed_book: 문자열 인덱싱 (Indexing)**  
- 문자열의 개별 문자에 접근할 때 사용  
- 인덱스는 0부터 시작, 음수는 뒤에서부터  

**:closed_book: 문자열 슬라이싱 (Slicing)**  
- 문자열의 일부 조각을 잘라내는 기능  
- `문자열[시작:끝]` → 끝 인덱스는 포함하지 않음
```  
s = "Python"
s[1:4]   # 'yth'
s[:2]    # 'Py'
s[::2]   # 'Pto' (2칸씩 건너뜀)
```

**:closed_book: split()**  
- 문자열을 구분자(delimiter)로 나눠서 리스트로 반환  
- 기본 구분자는 공백
```
"a b c".split()          # ['a', 'b', 'c']
"1,2,3".split(",")       # ['1', '2', '3']
```

**:closed_book: strip()**  
- 문자열의 양쪽 공백(또는 지정 문자)를 제거  
```
"  hello  ".strip()      # 'hello'
"***hi***".strip("*")    # 'hi'
```

**:closed_book: join()**  
- 리스트나 튜플의 문자열 요소를 하나의 문자열로 결합  
```
",".join(['a', 'b', 'c'])  # 'a,b,c'
" ".join("hello")          # 'h e l l o'
```

**:closed_book: lambda 함수**  
- 이름 없는 한 줄짜리 함수  
- 주로 `map()`, `filter()`와 함께 사용  
```
square = lambda x: x ** 2
square(3)  # 9
```

**:closed_book: map() 함수**  
- 리스트 등의 각 요소에 함수 적용하여 새 객체 생성  
- 결과는 map 객체 → 보통 list()로 변환  
```
nums = [1, 2, 3]
list(map(lambda x: x * 2, nums))  # [2, 4, 6]
```
**:white_check_mark: 정규 표현식 (Regular Expressions)**  
문자열에서 특정 패턴을 찾거나 변환할 때 사용하는 표현 방식입니다.  
예를 들어, 이메일 주소, 전화번호, 날짜, 특정 형식의 문장을 찾거나 바꿀 때 유용합니다.  
- **데이터 검증**: 이메일, 전화번호, 우편번호 등의 형식 검사
- **텍스트 검색**: 특정 패턴의 단어 또는 문장 찾기
- **데이터 정제**: 불필요한 문자 제거, 특정 패턴 변환
- **자동화된 텍스트 처리**: 대량의 텍스트 데이터에서 원하는 정보를 추출  


**:white_check_mark: re 모듈**  
파이썬에서 정규 표현식을 사용하려면 **re 모듈**을 활용합니다.  
주요 함수는 다음과 같습니다:  
- re.match() → 문자열의 **시작**에서 정규식과 매칭되는지 확인
- re.search() → 문자열 **전체**에서 정규식과 매칭되는지 확인
- re.findall() → 정규식과 일치하는 **모든 부분을 리스트로 반환**
- re.sub() → 정규식에 매칭되는 부분을 새로운 문자열로 **대체**  

**:closed_book:스택(Stack)**  
- **후입선출(LIFO, Last In First Out)** 구조
- 가장 최근에 삽입된 데이터가 가장 먼저 삭제  

**:book: 스택의 특징**  
- **삽입(Insert)**: 스택의 맨 위에 데이터를 삽입
- **삭제(Delete)**: 스택의 맨 위에서 데이터를 삭제
- **탐색(Peek/Top)**: 스택의 맨 위 데이터를 확인  

**:closed_book: 큐(Queue)**  
- 큐는 **선입선출(FIFO, First In First Out)** 구조
- 가장 먼저 삽입된 데이터가 가장 먼저 삭제  

**:book: 큐의 특징**  
- **삽입(Enqueue)**: 큐의 끝에 데이터를 삽입
- **삭제(Dequeue)**: 큐의 맨 앞에서 데이터를 삭제
- **탐색(Front)**: 큐의 맨 앞 데이터를 확인  

**[정리]**  
- 스택(Stack) → LIFO(Last-In-First-Out)  
→ list.append(), list.pop()으로 구현 가능  
- 큐(Queue) → FIFO(First-In-First-Out)  
→ collections.deque() 사용하면 양쪽 삽입/삭제가 모두 빠름!  
→ deque.append(), deque.popleft() 추천  





