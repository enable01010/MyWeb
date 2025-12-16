# 授業目的
3DのTPSゲームの作成を通じて、ベクトルの考えや<br>
当たり判定の考えを身に着けて行きましょう。<br>

# プロジェクト
前回のMethodTextをそのまま使います。<br>

# 前回の要らないスクリプトの削除
前回は汎用のFPS、TPSをそれぞれ作ったため、FPS部分を削除します。<br>
下記のスクリプトをRemoveCompornentしてください。<br>
・CameraについているFPSCamera<br>
・PlayerについているFPSPlayer<br>

# キャラクターの動きの修正
前回のTPSカメラは汎用的にするために、<br>
カメラとキャラクターの向きが別々になるようにしていました。<br>
<br>
ただ、シューティングになると、カメラの向きに合わせて弾を撃つため、<br>
カメラとキャラクターの向きをあわせる必要があります。<br>
<img src="Image/3DTPS/PlayerMove.png"><br>

# カメラの中心位置の修正
前回のカメラはキャラクターが中心になるようになっていました。<br>
しかしTPSのシューティングにおいては、中心より少し下に無いと行けないため、<br>
設定を変更します。<br>

1. Playerの中のCameraTargetの位置をx0,y2,z0に変更<br>
2. CameraのTPSCameraのTargetをView→CameraTargetに変更<br>
<img src="Image/3DTPS/CameraView0.png"><br>
<img src="Image/3DTPS/CameraView1.png"><br>

# 弾と、射撃の作成
弾の作成(スクリプト)<br>
<img src="Image/3DTPS/Bullet0.png"><br>
<img src="Image/3DTPS/Bullet1.png"><br>
<br>
弾の作成（Unity操作）<br>
1. 空オブジェクトを生成して名前をBulletにする<br>
2. その中に、3D→Sphereを生成して名前をViewにする<br>
3. BulletにBulletスクリプトをアタッチする<br>
4. Bulletオブジェクトをプレハブにする<br>
<img src="Image/3DTPS/BulletView0.png"><br>
<img src="Image/3DTPS/BulletView1.png"><br>
<br>
<br>
<br>
射撃の作成(スクリプト)<br>
<img src="Image/3DTPS/Shooter0.png"><br>
<img src="Image/3DTPS/Shooter1.png"><br>
<br>
射撃の作成（Unity操作）<br>
1. PlayerにTPSShooterをアタッチする<br>
2. Playerの中に空オブジェクトを作成し名前をBulletStartPosにする<br>
3. BulletStartPosの場所をx0,y0.5,z1にする<br>
4. PlayerのTPSShooterのBulletStartPosに上のやつをシリアライズする<br>
1. <img src="Image/3DTPS/ShooterView0.png"><br>
<img src="Image/3DTPS/ShooterView1.png"><br>