# Day6 

* <기술적인 도전>
  * 본인의 점수 및 순위: LB점수 - 0.6618, 164등

* 검증 전략
  * 1. 제공된 train 데이터셋이 충분히 많다고 판단하여 10%만 validation data로 사용하여 hyperparameter tuning을 하였습니다.

* 사용한 모델 아키텍처 및 하이퍼파라미터
  * 1. 아키텍처: 2-layer CNN
	    * A. LB 점수: 0.3821
	    * B. training time augmentation
		    *- Resize, HorizontalFlip, ShiftScaleRotate, HueSaturationValue, RandomBrightnessContrast, GaussNoise, Normalize
	    * C. img_size = 224 x 224
	    * D. optimzier: Adam
	    * E. scheduler: None
	    * F. 5 X TTA
	    * G. 추가시도
		    * - CNN layer의 filter 개수와 activation function을 변경하여 약간의 성능 향상이 있었습니다.
