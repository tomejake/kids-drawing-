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

### android:dither="true": 이미지 조정 RGB 로 만든 이미지를 사용자가 ARGB 환경에서도 볼 수 있게 함

### LinearLayout 을 불러오면 선형으로 나열된 데이터를 쉽게 찾아올 수 있다.
예시)
``` kotlin
    val linearLayoutPaintColors:LinearLayout = findViewById(R.id.ll_paint_colors)
    mImageButtonCurrentPaint = linearLayoutPaintColors[1] as ImageButton
```

## 권한부여
1. manifests/ 에서 기능 추가
    <uses-permission android:name="android.permission.CAMERA"/> 추가 (예시는 카메라)

2. MainActivity 에서 선언 후 구현
    private val cameraResultLauncher: ActivityResultLauncher<String> =
            registerForActivityResult(ActivityResultContracts.RequestPermission()) {
                isGranted ->
                if(isGranted){
                    Toast.makeText(this, "Permission granted for camera", Toast.LENGTH_LONG).show()
                } else {
                    Toast.makeText(this, "Permission denied for camera", Toast.LENGTH_LONG).show()
                }
            }

