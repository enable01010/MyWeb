# 前回のプログラムの修正
## カメラのリコイル制御をコルーチンに変更
前回のプログラムだとリコイルの際に、カメラが一瞬で飛ぶので<br>
動きがカクカクしていて酔いやすいものだったと思います。<br>
なので、リコイルの制御を滑らかなものにしましょう。<br>
<img src="Image/3DTPS/CameraRicoileCor.png"><br>

## エイムの作成
カメラのエイムを作成していきましょう。<br>
<img src="Image/3DTPS/CameraAim0.png"><br>
<img src="Image/3DTPS/CameraAim1.png"><br>
<img src="Image/3DTPS/CameraAim2.png"><br>
この処理を追加するとマウスの右ボタンを押し続けてる間、
スコープを覗き込んだような視界になると思います。<br>

## UIがプレイヤーの方を向くように修正(ビルボード)
現状だとエネミー（仮）の横側に行くとHPバーが見えなくなるような状態なのでそれを修正しましょう。<br>
<img src="Image/3DTPS/PlayerMove.png"><br>

Unityでの操作<br>
1.Enemyの子階層にあるHpBarにBuilbordをアタッチ<br>


# モデルの適応
マップやPlayerが簡素過ぎてわかりにくいので、モデルに置き換えて行きましょう。<br>
<br>
Unityの操作<br>
1.　Publicの谷山講師/12_23にUnityパッケージがあるので、それを適応してください。<br>
2.　シーン上にPrefab/LevelDesertを配置してください（x0y0z0)<br>
3.　シーン上のPlaneを削除してください。<br>
4.　シーン上のPlayerについているShooter系のやつを好きなやつ１個残してRemoveしてください。<br>
5.　Playerの中のViewを削除してください。<br>
6.　Playerの中にPrefab/Demo_Tankをいれてください。<br>
7.　Player/Demo_Tank/TankTurretの子階層にBulletStartPosを移動してください。<br>
8.　BulletStartPosとCameraPosを適切な位置にしてください。<br>

## プレイヤー挙動の変更
すみません、プレイヤーが人間想定で作ってたのですが<br>
アニメーションがゴタゴタしそうだったので、戦車に変えました。<br>
それに合わせた修正をお願いします。<br>
<img src="Image/3DTPS/SenshaMove0.png"><br>
<img src="Image/3DTPS/SenshaMove1.png"><br>

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
　