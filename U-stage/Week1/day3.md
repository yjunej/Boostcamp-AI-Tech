# Day 3 - 파이썬 기초 문법 II

## Python Data Structure
* Collections
  * deque
    * Stack과 Queue지원, 빠른 자료 저장 방식
    * rotate, reverse 지원
    * 효율적인 메모리 구조
  * OrderedDict
    * python 3.6 부터 dict에서도 순서 보장
  * defaultdict
    * 함수 형식으로 초기값 설정 가능
  * Counter
    * Sequence type element들의 갯수를 dict 형태로 반환
  * namedtuple
    * tuple 형태로 데이터 구조체를 저장
    * Point = namedtuple('Point',['x','y'])
  
  

## Pythonic code

* nested list comprehension
  * result = [i+j for i in word_1 for j in word_2]
    * word_2 loop first
  * result = [ [i+j for i in case_1] for j in case_2]
    * case_1 loop first
* lambda
  * f = lambda x,y: x+y, f(1,4) = 5
    * 어려운 문법, 해석, 테스트의 어려움으로 권장하지 않음
* iterable object
  * iter(), next()를 사용하여 iterable 객체를 iterable object로 사용
* generator
  * iterable object를 특수한 형태로 사용하는 함수
  * element가 사용되는 시점에 값을 메모리에 반환
  * yield를 사용하여 하나의 element를 반환
  * gen_ex = (n*n for n in range(500))
  * list 타입의 데이터 반환 함수는 generator 사용 권장
  * 큰 데이터 처리에 어려움이 없어 파일데이터에도 유리
* asterisk
  * 개수가 정해지지 않은 변수를 함수의 인자로 사용하는 방법
  * 입력된 값은 tuple type으로 사용
  * 오직 한 개만 마지막 parameter 위치에 사용가능
  ```
  def asterisk_test(a, b,args):
    return a+b+sum(args)
  print(asterisk_test(1, 2, 3, 4, 5))
  ```
  * 키워드 가변인자
  ```
  def kwargs_test_2(**kwargs):
    print(kwargs)
  print("First value is {first}".format(**kwargs))
  print("Second value is {second}".format(**kwargs))
  print("Third value is {third}".format(**kwargs))
  
  def kwargs_test_3(one,two,*args,**kwargs):
    print(one+two+sum(args))
  print(kwargs)
  kwargs_test_3(3,4,5,6,7,8,9, first=3, second=4, third=5)
  ```





 ## 피어섹션
 
 * 피어
   * 김광호, 김현우, 오승택, 정영준, 한웅희
 * 회의시간
   * 14:00 ~ 15:30
 * 회의내용
   * 구글 docs에 회의록 작성하기
   * ice-breaking time 
   * 앞으로 회의 계획 확정
   * 조교님께 드릴 질문 정리
   * day2 수업에 관한 정보 공유
 









 
 
  


  
