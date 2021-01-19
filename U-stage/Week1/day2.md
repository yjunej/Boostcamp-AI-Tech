# Day 2 - 파이썬 기초 문법

## Variables

* a = 5 : a라는 변수에 5라는 값을 넣는다.
* 폰노이만 아키텍쳐
  * 입력값을 메모리에 저장, CPU가 순차적으로 정보를 해석
* 선언되는 순간 물리적인 공간이 할당
* 부동소수점 문제
  * 실수 -> 이진수 변환 과정에서 반올림 오차 발생


## Function & Console I/O

* print formatting
  * %string
    * print('%s %s' %('one','two')
  * foramt
    * print('{} {}'.format('one','two'))
  * fstring
    * print(f'{one} {two}')

## Conditionals and Loops

* x==y : 값 동일
* x is y: 메모리 주소 동일
* 반복문 아래 else를 사용하여 반복문 종료 후 else 블록 실행 (break시 skip)

## String and advanced function concept

* a.capitalize(): 문자열 a의 첫 문자를 대문자로 변환
* a.title(): 문자열 a를 제목 형태로 변환 (띄어쓰기 후 첫 글자만 대문자)
* a.startswith('abc'): 문자열 a가 'abc'로 시작하는지 여부 반환
* a.endswith('abc'): 문자열 a가 'abc'로 끝나는지 여부 반환
* Scope
  * a라는 변수를 인자로 받는 함수 내에서 a를 선언: 지역 변수로 새로운 메모리 공간에 선언
  * global 키워드를 사용하여 위와 같은 경우에서 전역 변수 a의 값을 변경 가능
* 코딩 컨벤션
  * 사람의 이해를 돕기위한 코드 작성에서의 규칙
  * 일관성이 중요
  * 명확한 규칙은 존재하지 않음
  * flake8 or black 모듈로 체크 또는 변환이 가능



 ## 피어섹션
 
 * 피어
   * 김광호, 김현우, 오승택, 정영준, 한웅희
 * 회의시간
   * 14:00 ~ 15:30
 * 회의내용
   * 전체적인 계획을 수정
   * 초반부에는 각자 학습일지를 공유하고 보면서 서로 학습하기
   * ice breaking을 위한 개인적인 질문 시간 가지기
   * 좋은 자료 있으면 서로 공유하기
   * 새로운 논문 리뷰나 모델학습 보다 주어진 edwith 학습에 초점 맞추어 성장하기
 









 
 
  


  
