# ベクトルを使ったゲーム製作

# 授業目的
ベクトルは2D、3D問わず必要な知識になります。<br>
今まではUnityに頼りつつ雰囲気でできていたものも多いと思いますが、<br>
ここで一度、知識としてベクトルを身につけて、ある程度理解できるようになりましょう。<br>

# 今日作成していくゲーム
<!-- 動画 -->
<iframe width="560" height="315" src="https://youtu.be/xXXEHgmp0O4?si=2kPhlqi2sKIDxn0y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

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
## 移動範囲を作成する
## プレイヤーの移動プログラムを作成する
## 玉の移動プログラムを作成する
## プレイヤーのHP管理用のプログラムを作成する
## 玉のあたり判定用プログラムを作成する
## 回復アイテムを作成してみる
## 玉の移動方向にバリエーションをつける
## 玉の発射を制御するスクリプトを作成する（次の授業になると思います。）