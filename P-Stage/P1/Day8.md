# Day8

* 2. 아키텍처: ResNext
	* A. LB점수: 0.6618
	* B. training time augmentation
	   *- Resize, HorizontalFlip, ShiftScaleRotate, HueSaturationValue, RandomBrightnessContrast, GaussNoise, Normalize
	* C. img_size = 224 x 224
	* D. 4 X TTA
	* E. scheduler: ReduceOnPlateau
	* F. optimizer: Adam
	* G. 기타 시도
	  * - 모델의 성능을 높이기 위하여 epoch을 늘리고 개수가 적은 class에 대한 예측을 더 잘하기 위해 Loss function에 클래스 수가 적을수록 가중치를 주어 학습하자 성능이 매우 크게 향상 되었습니다. (0.3944 - 1 epoch, 0.6618 - 5 epoch, weighted loss)

* 앙상블방법
  * 1. 하나의 모델을 구성하고 hyperparameter tuning을 하는데 많은 시간을 사용하여 앙상블기법을 마지막에 적용하지 못하였습니다.
