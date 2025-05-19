상승/하강/정지/긴급/경고 상황과 같이 상태가 변하는 상황이 있을 것이다.

우선 상태 정의에 대해 다시 한번 깊게 고민해 보자

왜 UserMotionState라고 정의했는가?
- 유저의 의도, 목적에 따라 제어되는 시스템이기 때문에.
- 문제가 발생한 뒤 다시 동작할 필요가 없다.
- UserMotionState == MotionState라고 봐도 되
  - MovingUp = UserUp
  - MovingDown = UserDown
  - Stop = UserStop
- User 상태를 명시적으로 갖고 있을 필요가 있나?

Emergency와 Warning state는 어떻게 처리할 것인가?
- Emergency를 true/false로?
- 새로운 state로?

- UserState가 EmergencyState라는 건 이상해
- SystemState가 EmergencyState라는 건 가능해