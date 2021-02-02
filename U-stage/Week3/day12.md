
# Day 12 - 최적화

## Optimization
- Generalization
  - 일반화 
  - Generalization gap: train set과 test set 사이의 성능차이
  - Underfitting: 가중치가 데이터를 충분히 설명하지 못하는 상태
  - Overfitting: 데이터에 과적합하여 test set에서 성능이 좋지 않은 상태
  - CV: train data를 n fold로 나누어 1 fold를 순차적으로 test set(valid set)으로 사용하여 퍼포먼스를 평균내어 score 도출
  - Bias: 중심에서 떨어진 정도, 편향
  - Variance: 비슷한 데이터에 대한 결과의 흩어진 정도, 분산
  - Low Bias & Low Variance == Best
  - Bootstraping: Train set 에서 랜덤하게 일정 수의 표본을 뽑아 반복적으로 training
  - Bagging: 다수의 같은 모델이 bootstrap sampling된 표본으로 훈련 -> voting
  - Boosting: 틀린 예측에 대해 가중치를 두어 학습하며 update
- Gradient Descent
  - Momentum: moving average
  - Nesterov accelerated gradient: Look ahead gradient
  - Adagrad: larger updates for infrequent
  - Adadelta: No LR
  - RMSprop: adaptive LR method
  - Adam: RMSprop+Momentum
- Regularization
  - Ealry Stopping: 조기 종료로 인한 Overfitting 방지
  - Parameter Norm Penalty: L1 or L2 등 가중치값들의 Norm을 cost function에 추가하여 규제
  - Data Augmentation: 데이터를 증식시켜 Overfitting 해결
  - Noise Robustness: Noise를 추가한 데이터를 통해 Train data의 특정 분포에 집중하여 과적합 되는것을 방지
  - Label Smoothing: 다른 Label의 데이터를 혼합시켜 기법에 따라 혼합된 Label 할당
  - Dropout: Bagging과 비슷한 원리
  - BN: 층이 깊어짐에 따른 Covariance shift 방지


과제 모델 구현 
```

class Model(nn.Module):
    def __init__(self,name='mlp',xdim=1,hdims=[16,16],ydim=1):
        super(Model, self).__init__()
        self.name = name
        self.xdim = xdim
        self.hdims = hdims
        self.ydim = ydim

        self.layers = []
        prev_hdim = self.xdim
        for hdim in self.hdims:
            self.layers.append(nn.Linear(
                # FILL IN HERE
            ))
            self.layers.append(nn.Tanh())  # activation
            prev_hdim = hdim
        # Final layer (without activation)
        self.layers.append(nn.Linear(prev_hdim,self.ydim,bias=True))

        # Concatenate all layers 
        self.net = nn.Sequential()
        for l_idx,layer in enumerate(self.layers):
            layer_name = "%s_%02d"%(type(layer).__name__.lower(),l_idx)
            self.net.add_module(layer_name,layer)

        self.init_param() # initialize parameters
    
    def init_param(self):
        for m in self.modules():
            if isinstance(m,nn.Conv2d): # init conv
                nn.init.kaiming_normal_(m.weight)
                nn.init.zeros_(m.bias)
            elif isinstance(m,nn.Linear): # lnit dense
                nn.init.kaiming_normal_(m.weight)
                nn.init.zeros_(m.bias)
    
    def forward(self,x):
        return self.net(x)

```

# 피어세션
## To Do List
- 수업중 모르겠던거나 유용하다고 생각하는것 공유
- 다른 캠퍼들이 올린 질문 보기 - 답변이 올라오지 않은 질문의 경우 다음날 토의 결정
- futher question: pytorch 문서 보기

## Question
- 강화학습 공부법
- 수업 내용에 대하여
- Tensorflow vs Pytorch













 
 
  


  
