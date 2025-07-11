MotionState와 Kinematics의 관계

MotionState는 State 변화를 알고 있고
Kinematics는 포지션,속도,가속도 등을 알고 있다.

MotionState가 Kinematics에 State 변화에 따른 다음의 정보를 알려줘야 한다.
- 가속/감속의 시작인지?
- 시작 시간: 이건 시간으로 받아오면 됨
- 가속, 감속 시간

Kinematics는 가감속 변수를 설정할 수 있는 메서드를 제공한다.
- StartAccelation(speed,accel_time)
- StartDecelation(speed,decel_time)

MotionState에서 State 변화에 따라 위 메서드를 호출한다.

---
각 모듈은 State 변화에 따라 호출되어야 하는 함수를 제공하고,
MotionState에서 해당 함수를 호출하는것이 정석으로 보인다.

---
Target position, Target speed는 어디서 보유하는 것이 좋을까?


GetNextVelocity
1. get remain distance.
2. get step count with speed and distance.
3. Get next point.
4. get distance to next point.
5. Cal base speed with step distance and period.

속도는 누가 증가 시키지?