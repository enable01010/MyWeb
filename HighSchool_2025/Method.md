# 本日の授業内容

本日は座学強めの授業になります。<br>
<br>
Unityで使える関数についての授業です。<br>
本日は、なにかのゲームを作るというよりかは、<br>
Unityのプログラムでこんな事できるよ～みたいなものの紹介になります。<br>
<br>
自分の制作の際に、こんな機能あったな～と思い出して、<br>
調べて使えるようになることを目指しましょう。<br>
<br>
# プロジェクト立ち上げ
Unity6　Univarsal 3D プロジェクト名　MethodTestで作成<br>

# 汎用的なプログラムの紹介

## ＜MonoBehaviour ライフサイクル・コールバック＞

Awake()　//　オブジェクトができてすぐ<br>
Start()　//　Awakeの後<br>
<br>
Update()　//　毎フレーム<br>
LateUpdate()　//　Updateの直後<br>
FixedUpdate()　//　設定した秒数に一回（通常は0.02秒）<br>
<br>
OnEnable()　//　SetActiveで切り替えたとき）<br>
OnDestroy()　//　オブジェクトが破棄される直前<br>


## ＜Transform 関係＞
transform.position　//絶対座標<br>
transform.localPosition　//相対座標<br>
transform.rotation　//絶対回転Quortaion<br>
transform.localRotation　//相対回転Quortaion<br>
transform.eulerAngles　//相対回転Vector3<br>
transform.localScale　//大きさ<br>
<br>
transform.LookAt(Transfrom)　// 特定の方向を向ける<br>

## ＜GameObject 関係＞
gameObject.SetActive(bool)　//オブジェクトの有効無効を切り替える<br>
gameObject.activeSelf　//現在オブジェクトが有効か無効か判定する<br>
<br>
GetComponent<T>()　//特定のコンポーネントを取得する<br>
AddComponent<T>()　//特定のコンポーネントを追加する<br>
GetComponentInChildren<T>() //子オブジェクトの中の特定のコンポーネントを取得する<br>
GetComponentInParent<T>() //親オブジェクトの中の特定のコンポーネントを取得する<br>
<br>
Destroy(Object)　//オブジェクトを破棄する<br>
Instantiate(Object)　//オブジェクトを生成する<br>

# 汎用的なプログラムを作ってしまおう
## 汎用カメラ　TPS
<img src="Image/HighSchool_2025/Method/TPSCamera1.png"><br>
<img src="Image/HighSchool_2025/Method/TPSCamera2.png"><br>
<img src="Image/HighSchool_2025/Method/TPSCamera3.png"><br>

## 汎用カメラ　FPS
<img src="Image/HighSchool_2025/Method/FPSCamera.png"><br>

<!--
## 汎用キャラクターの移動　TPS
<img src="Image/HighSchool_2025/Method/FPSCamera.png"><br>

## 汎用キャラクターの移動　FPS
<img src="Image/HighSchool_2025/Method/FPSPlayerMove1.png"><br>
<img src="Image/HighSchool_2025/Method/FPSPlayerMove2.png"><br>

-->