# Tensorflow. Keras



## Callback

- **EarlyStopping**

  : 모델을 더 이상 학습을 못할 경우(loss, metric등의 개선이 없을 경우), 학습 도중 미리 학습을 종료시키는 콜백함수

  출처: https://deep-deep-deep.tistory.com/55 [딥딥딥:티스토리]

  - monitor 
    * 학습 조기 종료를 위해 관찰하는 항목
    * val_loss, val_accuracy 주로 사용
    * val_loss < default
  - min_delta
    * 개선되고 있다고 판단하기 위한 최소 변화량
    * min_delta보다 작으면 개선이 없다고 판단
    * default = 0

  + patience
    - 개선이 안 될 경우 몇번의 epoch를 기다릴지
  + mod
    * 개선이 없다고 판단하는 기준을 결정
    * auto : monitor에 따라 자동 판단
    * min : 감소하는 것을 멈출 때, `val_loss`에 사용
    * max : 증가하는 것을 멈출 때, `val_accuracy`에 사용
  + baseline
    - 모델이 달성해야 하는 최소한의 기준값
    - patience 이내에 모델이 baseline보다 개선되지 않을시 training 중단
  + restore_best_weights
    - True : Training이 끝난후 값이 가장 좋았을때의 weight로 복원.
    - False : 마지막 weight를 그대로 유지

---

- **ModelCheckpoint**

  : 모델을 저장할 때 사용되는 콜백함수

  - filepath
    - 모델을 저장할 경로

  - monitor 
    * 모델을 저장할 때 기준이 되는 값
  - verbose
    * 0 : 화면에 표시하지 않고 바로 저장
    * 1 : 모델이 저장될 때 화면에 표시

  + save_best_only

    - True : monitor 되고 있는 값 기준, 제일 좋은 값을 저장

    - False : 매 epoch마다 모델이 저장

  + save_weight_only

    * True : 모델의 weight만 저장

    * False : 모델의 레이어, weight 모두 저장

  + mode 

    * auto : monitor에 따라 자동 판단
    * min : 감소하는 것을 멈출 때, `val_loss`에 사용
    * max : 증가하는 것을 멈출 때, `val_accuracy`에 사용

  + save_freq

    - epoch : 매 epoch마다 모델 저장
    - 숫자(int) : 숫자만큼의 batch 진행 후 저장

- 

## models

- Sequnetial()



## layers

- LSTM







- Dense

