# 授業目的
3DのTPSゲームの作成を通じて、ベクトルの考えや<br>
当たり判定の考えを身に着けて行きましょう。<br>

# プロジェクト
Unity6 Universal3D プロジェクト名　3DTPS

# カメラの作成
まずはカメラの作成を行います。<br>
下記のスクリプトを作成してください。<br>
<img src="Image/3DTPS/Cam2_0.png"><br>
<img src="Image/3DTPS/Cam2_1.png"><br>
<img src="Image/3DTPS/Cam2_2.png"><br>
<img src="Image/3DTPS/Cam2_3.png"><br>

# キャラクターの動きの作成
次にカメラの向きに合わせて動くようにプレイヤーの移動処理を作成しましょう。<br>
<img src="Image/3DTPS/PlayerMove2_0.png"><br>
<img src="Image/3DTPS/PlayerMove2_1.png"><br>
<img src="Image/3DTPS/PlayerMove2_2.png"><br>
<img src="Image/3DTPS/PlayerMove2_3.png"><br>
# 弾と、射撃の作成
弾の作成(スクリプト)<br>
<img src="Image/3DTPS/Bullet0.png"><br>
<img src="Image/3DTPS/Bullet1.png"><br>
<br>
弾の作成（Unity操作）<br>
1. 空オブジェクトを生成して名前をBulletにする<br>
2. その中に、3D→Sphereを生成して名前をViewにする<br>
3. ViewのコライダーのIsTriggerをOnにする<br>
4. BulletにBulletスクリプトをアタッチする<br>
5. Bulletオブジェクトをプレハブにする<br>
6. Bulletオブジェクトを削除する<br>
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
5. PlyaerのBulletPrefに先ほどプレハブにしたBulletを入れる<br>
<img src="Image/3DTPS/ShooterView0.png"><br>
<img src="Image/3DTPS/ShooterView1.png"><br>


# 敵のダメージを受ける処理の作成
まず、以前まで使っていたHPBar.csをこのプロジェクトに持ってきてください。<br>
VectorGame等<br>
その後下記スクリプトの作成をして下しさい<br>

エネミーの作成(スクリプト)<br>
<img src="Image/3DTPS/EnemyHit.png"><br>
<br>
エネミーの作成(Unity操作)<br>
1. 空オブジェクトを生成して名前をEnemyにする<br>
2. その中に、3D→Cubeを生成して名前をViewにする<br>
3. EnemyにEnemyHitスクリプトをアタッチする<br>
4. Enemyの中にUI→Canvasを作成する<br>
5. CanvasのCanvasのRenderModeをWorldSpaceにする<br>
6. Canvasの中に空のオブジェクトを作成して名前をHpBarにする
7. 以前と同じような形でHPBarを作成する
8. EnemyHitのHPBarに作成したHPBarをシリアライズする
<img src="Image/3DTPS/EnemyHitView0.png"><br>
<img src="Image/3DTPS/EnemyHitView1.png"><br>


# 射撃方法の変更
一般的にシューター系のゲームでは射撃にクルールタイムがあることが多いと思います。<br>
現状はクリックできたらマイフレーム打てるようになっているので、射撃にクールタイムを設けましょう。<br>
Shooter.csを下記のように変更してください。<br>
<img src="Image/3DTPS/Shooter2_0.png"><br>
<img src="Image/3DTPS/Shooter2_1.png"><br>
<img src="Image/3DTPS/Shooter2_2.png"><br>
<br>
他にも連射の銃や3連タップの銃など作成しましょう。<br>
連射銃<br>
<img src="Image/3DTPS/ShooterAuto0.png"><br>
<img src="Image/3DTPS/ShooterAuto1.png"><br>
<img src="Image/3DTPS/ShooterAuto2.png"><br>
<img src="Image/3DTPS/ShooterAuto3.png"><br>
カメラのとこにも修正にも追加をします。<br>
<img src="Image/3DTPS/CameraShoot.png"><br>
<br>
3連タップ<br>
<img src="Image/3DTPS/ShooterTap0.png"><br>
<img src="Image/3DTPS/ShooterTap1.png"><br>
<img src="Image/3DTPS/ShooterTap2.png"><br>
<img src="Image/3DTPS/ShooterTap3.png"><br>
<img src="Image/3DTPS/ShooterTap4.png"><br>

<!--

カメラのリコイル制御をコルーチンに変更
エイムの処理を作成
エネミーがプレイヤーに向かって来る処理の作成
エネミーがプレイヤーに向かって弾を打つ処理の作成
プレイヤーの被弾処理
UIがプレイヤーの方向を向くように修正

# エイムの作成
右クリックを押してる間にエイムをするような処理を作成していきましょう。

# 攻撃方法の変更
　連射<br>
　エイム<br>

# 敵の部位別のダメージ
　キャラクターの実装<br>
　プログラムの実装<br>

# 弾の改善
　反動<br>
　移動エフェクト<br>
　着弾エフェクト<br>
　サウンド<br>
　オブジェクトプール<br>
　
# エネミーの挙動
# エネミーのポップ
# オンライン化

-->
　