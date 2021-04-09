# Ensemble

* Bagging
  * High Bias를 해결할 수 있음
  * 여러개의 Biased Model을 합쳐서 오버피팅을 줄인다.
  
* Voting
  * 여러 모델의 결과를 평균내서 사용한다.
  * 서로 다른 모델은 같은 에러가 아닌 클래스, 인스턴스 별로 다른 에러를 낸다.
  * Hard voting: predict label로 voting을 하는 것, 가장 높은 확률의 클래스만 고려
  * Soft voting: 각각의 모델의 확률을 보고 그것을 평균내어 선정
  * 소프트보팅이 성능이 일반적으로 좋다.
  
* Boosting
  * 잘못 예측한 것에 가중치를 주며 순차적으로 학습
  
* Cross Validation
  *  validation set을 바꿔가면서 사용
  * validation set의 분포를 버리지 않고 train 과정에 최소 1번이상 사용
  * K-fold 가능한 경우 모두 고려, 보통 K=5 이상
  * Stratified: imbalanced 클래스의 경우에 사용하면 좋다. class의 비율이 train set과 validation set의 같게한다.
  
* Hyperparameters
  * Loss
  * Hidden layer
  * k-fold
  * lr
  * Dropout
  * Regularization
  * Batch size
  
  * Hyperparameter optimization
    * 시간이 매우 많이 소모되나 크게 성능의 향상이 없는 경우가 있다.
    * Bayesian Optimization 많이 사용한다.
    * Optuna
