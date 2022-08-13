## 터치 관련 이벤트 조작
- onTouchEvent 활용
### 터치 이벤트 3개
- action done: 화면을 터치 했을때
- action move: 화면을 드래그 했을때
- action up: 손가락을 들었을때?

view 를 화면에 올리려면 layout 제약조건을 줘야함
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintLeft_toLeftOf="parent"
app:layout_constraintRight_toRightOf="parent"
app:layout_constraintTop_toTopOf="parent"