# Day 4 - 파이썬 기초 문법 III

## Python OOP

* Inheritance
  * 부모 클래스로 부터 속성과 Method를 물려받은 자식 클래스 생성
  ```
  class Person(object): # 부모 클래스 Person 선언
    def __init__(self, name, age, gender):
      self.name = name
      self.age = age
      self.gender = gender
    def about_me(self): # Method 선언
      print("저의 이름은 ", self.name, "이구요, 제 나이는 ", str(self.age), "살
      입니다.")
      
  class Employee(Person): # 부모 클래스 Person으로 부터 상속
    def __init__(self, name, age, gender, salary, hire_date):
      super().__init__(name, age, gender) # 부모객체 사용
      self.salary = salary
      self.hire_date = hire_date # 속성값 추가
    def do_work(self): # 새로운 메서드 추가
      print("열심히 일을 합니다.")
    def about_me(self): # 부모 클래스 함수 재정의
      super().about_me() # 부모 클래스 함수 사용
      print("제 급여는 ", self.salary, "원 이구요, 제 입사일은 ", self.hire_date,
      " 입니다.")
  ```
  
  * Polymorphism
    * 같은 부모를 상속받아도 자식 클래스에서 수정을 통해 이름이 같으나 다른 기능을 하는 함수 생성 가능
    
  * Visibility (Encapsulation)
    * Class를 설계할 때, 클래스 간 간섭/정보공유의 최소화
    * 캡슐을 던지듯, 인터페이스만 알아서 써야함
    ```
    class Inventory(object):
      def __init__(self):
        self.__items = []
    
    my_inventory = Inventory()
    print(my_inventory.__items) # Raise Error
    ```
    ```
    class Student:
        def __init__(self, name, marks):
          self.name = name
          self.marks = marks
          # self.gotmarks = self.name + ' obtained ' + self.marks + ' marks'
        @property
        def gotmarks(self):
          return self.name + ' obtained ' + self.marks + ' marks'
    ```

  * first-class objects
    * 파이썬의 함수는 일급함수
      * 변수나 데이터 구조에 할당이 가능한 객체
      * parameter로 전달이 가능, return 값으로 사용가능
  * Inner function
    * 함수 내에 또다른 함수 존재
  * closures
    * Inner function을 return 값으로 반환
    ```
    def tag_func(tag, text):
        text = text
        tag = tag
        def inner_func():
          return '<{0}>{1}<{0}>'.format(tag, text)
        return inner_func
    h1_func = tag_func('title', "This is Python Class")
    p_func = tag_func('p', "Data Academy")
    ```
  
  * decorator
    * 복잡한 closure 함수를 간단하게
  ```
  def star(func):
    def inner(*args, **kargs):
      print('*' * 30)
      func(*args, **kargs)
      print('*' * 30)
    return inner
  
  def percent(func):
    def inner(*args, **kargs):
        print('%' * 30)
        func(*args, **kargs)
        print('%' * 30)
    return inner
  
  @star
  @percent
  def printer(msg):
    print(msg)
  

  
  

## Module & Project

* 패키지
    * 모듈을 모아놓은 하나의 단위
* 모듈
    * .py 파일 1개
* 패키지 구조
    * root folder (game/)
        * __init__.py
        * image/
            * __init__.py
            * character.py
        * sound/
            * __init__.py
            * echo.py
        * stage/
            * __init__.py
            * main.py
            
* 폴더별로__init__.py 구성하기
    * __all__ = ['image','stage','sound']
* __main__.py 파일 만들기
```
from stage.main import game_start
from stage.sub import set_stage_level
from image.character import show_character
from sound.bgm import bgm_play
if __name__ == '__main__':
    game_start()
    set_stage_level(5)
    bgm_play(10)
    show_character()
```
    
* >python game 






 ## 피어섹션
 
 * 피어
   * 김광호, 김현우, 오승택, 정영준, 한웅희, 윤태현 조교님
 * 회의시간
   * 14:00 ~ 15:30
 * 회의내용
   * 조교님과 질의시간
   * ice-breaking time 
   * 다음 모더레이터 결정 (김현우)
 









 
 
  


  
