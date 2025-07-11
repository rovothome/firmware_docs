1. 모터 정보를 가져온다.
MotionController::ServoReadStatus1(&motor_l);

2. MotorStatus를 Update 한다.
UpdateMotorStatus(&motor_l, &motor_r);

- 모터 포지션 update한다.
- 모터 포지션 정보를 이용하여 모터의 xy 위치 및 Wally xy 위치를 update 한다.
- Remain distance를 update한다.
- 속도(motor_speed_after_fliter)를 이동평균으로 계산한다.
- 가속도를 이동평균된 속도를 이용하여 계산한다.
- 토크를 이동평균으로 계산한다.

닫는 상황에서
1. 속도를 50mm/sec 2000ms 가속도로 움직인다.
2. 속도가 안정된 상태에서만 토크 모델을 사용한다.
3. 속도가 정속일 때 사용하는 모델과 아닌 상태일 때 모델을 따로 사용한다.
4. 온라인 토크 모델을 통해 예측되는 토크를 계산한다.

온라인 토크 모델
1. Outlier 여부를 판단한다.
   1. 이 때 initize_count 이하이면 outlier라 판단하지 않는다.
2. Max learning_count 이하에선 outlier가 아니면 학습을 진행한다.
3. Outlier의 갯수가 연속적으로 3번 이상이면, 최종적으로 Outlier라고 판단한다.




---------
각도 Update 시점과 포지션 Update 시점이 다르다.
속도 노이즈를 줄이는 것과, 가속도를 추종하는 것에 대해 칼만 필터를 적용해 보자

모델링을 하고, 모델링을 짜달라고 해보자
