
# Day 7 - 경사하강법

* np.linalg.pinv
  * 선형회귀식을 찾는데 사용가능
```
for t in range(T):
 error = y - X @ beta
 grad = - transpose(X) @ error
 beta = beta - lr * grad
```
* 미분가능하고 볼록(convex)한 함수, 적절한 학습률과 학습횟수를 선택했을때 수렴이 보장
* 비선형 회귀문제의 경우 볼록하지 않은 목적함수를 가지면 수렴 보장 X
* 확률적 경사 하강법은 모든 데이터를 사용해서 업데이트 하는 대신 데이터 한 개 또는 일부 활용하여 업데이트
* SGD는 미니배치를 가지고 그래디언트 벡터를 계산
* SGD는 미니배치를 확률적으로 선택하여 목적식 모양이 변하게 된다.
* SGD로 out-of-memory 방지 및 CPU와 GPU의 업무 분할 가능


# 피어세션

- notion 정리 해보기<br>
- Latex 문법 : https://cleverway.tistory.com/20
- (Latex 문법 써보기)

- 내일 할것
  - 수업중 모르겠던거나 유용하다고 생각하는것 공유
  - 다른 캠퍼들이 올린 질문 보기
  - futher question
  - 근황 토크










 
 
  


  
