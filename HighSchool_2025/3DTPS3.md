# 前回のプログラムの復習

## エネミーの移動
※下記単体では動作しません。<br>
<img src="Image/3DTPS/EnemyMove.png"><br>

## エネミーの攻撃の作成
※下記単体では動作しません。<br>
<img src="Image/3DTPS/EnemyShoot0.png"><br>
<img src="Image/3DTPS/EnemyShoot1.png"><br>

## エネミーのAIの作成
<img src="Image/3DTPS/EnemyAi0.png"><br>
<img src="Image/3DTPS/EnemyAi1.png"><br>
<img src="Image/3DTPS/EnemyAi2.png"><br>
<img src="Image/3DTPS/EnemyAi3.png"><br>
<img src="Image/3DTPS/EnemyAi4.png"><br>
<img src="Image/3DTPS/EnemyAi5.png"><br>

## エネミーの作成（Unity）
1.　シーン上のEnemyのViewを削除<br>
2.　Enemyの中にPrefab/Demo_Tankをいれてください。<br>
3.　空オブジェクトを作成して、名前をBulletStartPosにしてください。<br>
4.　BulletStartPosをTankTurretの子階層に入れてください<br>
5.　EnemyにEnemyMove,EnemyShoot,EnemyAiをアタッチしてください。<br>
6.　EnemyShootのBulletPrefにPrefab/Bulletを入れてください<br>

# エネミーが特定の場所を徘徊するようにする
エネミーが特定の位置を行ったり来たりしながら、<br>
プレイヤーを探す挙動をするように変更しましょう。<br>
イメージとしてはメタルギアソリッドの敵キャラみたいなNPCです。<br>
まずはEnemyPatrolのスクリプトを作成してください。<br>
<img src="Image/3DTPS/Patrol0.png"><br>
<img src="Image/3DTPS/Patrol1.png"><br>
<img src="Image/3DTPS/Patrol2.png"><br>
<img src="Image/3DTPS/Patrol3.png"><br>
<br>
次にEnemyAiのスクリプトを修正してください。<br>
<img src="Image/3DTPS/AiPatrol0.png"><br>
<img src="Image/3DTPS/AiPatrol1.png"><br>
<img src="Image/3DTPS/AiPatrol2.png"><br>
<br>
Unityでの操作<br>
EnemyにEnemyPatrolをアタッチする<br>
EnemyのEnemyAiにリセットをかける<br>
空のオブジェクトを作成して名前をEnemyMovePosにする<br>
EnemyMovePosの子オブジェクトに空オブジェクトを複数作成して、移動してほしい経路に設置する<br>
EnemyのEnemyPatrolのシリアライズに作成した子オブジェクトをアタッチする<br>

# プレイヤーを見失った後にすぐパトロールに戻るのを修正
現在のエネミーはプレイヤーが物陰に隠れるとすぐにパトロールの軌道に戻ってしまいます。<br>
プレイヤーを見失った所までは追跡するように修正しましょう。<br>
<img src="Image/3DTPS/LostMove0.png"><br>
<img src="Image/3DTPS/LostMove1.png"><br>
<img src="Image/3DTPS/LostMove2.png"><br>
<img src="Image/3DTPS/LostMove3.png"><br>
<img src="Image/3DTPS/LostMove4.png"><br>
<img src="Image/3DTPS/LostMove5.png"><br>
<img src="Image/3DTPS/LostMove6.png"><br>
<img src="Image/3DTPS/LostMove7.png"><br>
<img src="Image/3DTPS/LostMove8.png"><br>
<img src="Image/3DTPS/LostMove9.png"><br>

# プレイヤー側にあたり判定をつける
Publicの谷山講師/1_20にエフェクトがあるのでそれをダウンロドしてください。<br>_

<img src="Image/3DTPS/PlayerHit0.png"><br>
<img src="Image/3DTPS/PlayerHit1.png"><br>

fxにはプレハブの2番を登録してください。<br>

# 敵にもがあたったときにFxを発生させる
<img src="Image/3DTPS/PlayerHit0.png"><br>
<img src="Image/3DTPS/PlayerHit1.png"><br>

fxにはプレハブの2番を登録してください。<br>

# 玉を打つ時にFxをつける
<img src="Image/3DTPS/ShooterFx0.png"><br>
<img src="Image/3DTPS/ShooterFx1.png"><br>

fxにはプレハブの1番を登録してください。<br>

# 敵が攻撃を受けた時にそっちに向かって来るようにする
BulletHit
<img src="Image/3DTPS/BulletHitAi0.png"><br>
EnemyAi
<img src="Image/3DTPS/EnemyAiHit0.png"><br>
<img src="Image/3DTPS/BulletAi0.png"><br>


<!--

# エネミーの処理の作成
列挙体（Enum）を使ってステート管理を使った。


エネミーがプレイヤーに向かって来る処理の作成
エネミーがプレイヤーに向かって弾を打つ処理の作成
プレイヤーの被弾処理

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
　