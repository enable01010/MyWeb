# ベクトルを使ったゲーム製作

# 授業目的
ベクトルは2D、3D問わず必要な知識になります。<br>
今まではUnityに頼りつつ雰囲気でできていたものも多いと思いますが、<br>
ここで一度、知識としてベクトルを身につけて、ある程度理解できるようになりましょう。<br>

# 今日作成していくゲーム
<!-- 動画 -->
<iframe width="560" height="500" src="https://www.youtube.com/embed/xXXEHgmp0O4?si=ouNIdFQE6UhvttYo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# ベクトルとは
"向き"と"大きさ"のデータの事です。<br>
例えばUnityでよく使うTransform.positionは原点（0.0.0）からの向きと大きさ（距離）になります。<br>
又、RigidBody等で使うAddForce()も、向きと大きさを決めて力を伝えています。<br>

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 補足：</strong><br>
  Vector3　がすべて向きと距離というわけではありません。<br>
  便利だからという理由で、floatが三つ並ぶような"角度"などにも使われています。<br>
</div>

# ベクトルがゲームにどのように使われているか
オブジェクトの位置・向き<br>
オブジェクトどうしの距離<br>
オブジェクトの移動<br>
角度を求める<br>

# ゲームの作成
Unity6　Universal2D　タイトル：VectorGame <br>
でUnityのプロジェクトを作成してください。<br>

## 背景を黒色にする
カメラのEnviromentにあるBackgroundを黒色にしましょう。<br>
<img src="Image/HighSchool_2024/VectorCameraSetting.png"><br>

## 移動範囲を作成する
画像と同じ階層になるようにオブジェクトを作成してください。<br>
<img src="Image/HighSchool_2024/AreaHieralky.png"><br>
<img src="Image/HighSchool_2024/AreaIns.png"><br>
<img src="Image/HighSchool_2024/FrameIns.png"><br>
<img src="Image/HighSchool_2024/InnerIns.png"><br>

## プレイヤーの移動プログラムを作成する
Publicに本日の画像データが入っています。それを取り込んでください。<br>
\\10.80.100.100\Public\07_24年入学生用\プログラマー\高等部３年制ゲームプログラマー専攻\谷山講師\10.03データ\Image<br>
そうしたらPlayerMove.csを作成して、下記のプログラムを作成してください。<br>
<img src="Image/HighSchool_2024/PlayerMove.png"><br>
<br>
プログラムができたらPlayerのオブジェクトを作成します。<br>
<img src="Image/HighSchool_2024/PlayerHie.png" ><br>
<img src="Image/HighSchool_2024/PlayerIns.png" ><br>
<img src="Image/HighSchool_2024/PlayerViewIns.png"><br>
<img src="Image/HighSchool_2024/PlayerScene.png"><br>

実行してみて動けたらOKです。<br>

## 玉の移動プログラムを作成する
下記2つのプログラムを作成してください。<br>
BulletMove.cs<br>
BulletPlayerDirSelecter.cs<br>
<img src="Image/HighSchool_2024/BulletMove.png"><br>
<img src="Image/HighSchool_2024/BulletPlayerMoveDirSelector.png"><br>
できたらBulletのオブジェクトを作成します。<br>
<img src="Image/HighSchool_2024/BulletPlayerDirHie.png"><br>
<img src="Image/HighSchool_2024/BulletPlayerDirIns.png"><br>
<img src="Image/HighSchool_2024/BulletPlayerDirView.png"><br>
<img src="Image/HighSchool_2024/BulletPlayerDirScene.png"><br>

<br>
弾はPlayerの方向に動くようになったが、あたりの処理はしていないと思います。<br>
<br>

## プレイヤーのHP管理用のプログラムを作成する
下記のプログラムを作成して、Playerにアタッチしてください。<br>
PlayerHit.cs<br>
<img src="Image/HighSchool_2024/PlayerHit.png"><br>
そうしたらPlayerのHp表示用のオブジェクトを作成します。<br>
Create→UI→Sliderでオブジェクトを生成して、写真の内容にインスペクターを修正してください。<br>
<img src="Image/HighSchool_2024/SliderHie.png"><br>
<img src="Image/HighSchool_2024/SliderBackgournd.png"><br>
<img src="Image/HighSchool_2024/SliderFillArea.png"><br>
<img src="Image/HighSchool_2024/SliderFill.png"><br>
<img src="Image/HighSchool_2024/PlayerHitIns.png"><br>

## 玉のあたり判定用プログラムを作成する
下記のスクリプトを作成してBulletのオブジェクトにアタッチしてください。<br>
<img src="Image/HighSchool_2024/BulletHit.png"><br>

## 回復アイテムを作成してみる
弾の処理を参考に回復アイテムを作ってみましょう。<br>

## 玉の移動方向にバリエーションをつける
弾の処理を参考に、シリアライズフィールドの方向に発射する玉を作ってみましょう。<br>

## 玉の発射を制御するスクリプトを作成する（次の授業になると思います。）