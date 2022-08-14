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
- 카메라 1개만 확인
    private val cameraResultLauncher: ActivityResultLauncher<String> =
            registerForActivityResult(ActivityResultContracts.RequestPermission()) {
                isGranted ->
                if(isGranted){
                    Toast.makeText(this, "Permission granted for camera", Toast.LENGTH_LONG).show()
                } else {
                    Toast.makeText(this, "Permission denied for camera", Toast.LENGTH_LONG).show()
                }
            }
- 여러 권한 확인
private val requestPermission: ActivityResultLauncher<Array<String>> = registerForActivityResult(ActivityResultContracts.RequestMultiplePermissions()){
        permissions ->
        permissions.entries.forEach {
            val perMissionName = it.key
            val isGranted = it.value

            if(isGranted){
                Toast.makeText(this, "Permission Grated", Toast.LENGTH_LONG).show()
                val pickIntent = Intent(Intent.ACTION_PICK, MediaStore.Images.Media.EXTERNAL_CONTENT_URI)
            } else {
                if(perMissionName == Manifest.permission.READ_EXTERNAL_STORAGE){
                    Toast.makeText(this, "Oops you just denied permission",
                        Toast.LENGTH_LONG).show()
                }
            }
        }
    }
3. AlertDialog 로 권한 검사

### ImageView.setImage(): 이미지 넣는 여러 방법들이 존재

## 코루틴 (coroutines)
- 백그라운드의 긴 작업이 이어질때도 사용자가 UI를 다룰 수 있도록 도와준다.
- 이전에는 백그라운드 긴 작업 발생시 화면이 멈추고 UI를 다룰 수 없었고, 5초 이상의 딜레이가 생기면 프로그램이 종료됐음
- 함수 fun 앞에 suspend 를 추가해서 선언

# 마지막 3개 영상 안봄