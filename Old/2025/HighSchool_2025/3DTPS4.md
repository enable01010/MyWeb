# 前回のプログラムの復習

## プロジェクトの進捗をあわせる
少し授業が続いて、進捗がバラバラになって来たので、プロジェクトを配布します。<br>
Publicの1/27にあるUnityパッケージをDLして、今までのプロジェクトにインポートしてください。<br>

## エネミーのあたり判定を分割する
現状のエネミーはどこに攻撃を受けても一定のダメージが入ると思います。<br>
FPSゲームやBossなどによくあるパーツ事にダメージが違うような処理を作成してみましょう。<br>
<br>
EnemyHitPart.csとEnemyHitMaster.csを作成してください。<br>
<img src="Image/3DTPS/EnemyHitMaster0.png"><br>
<img src="Image/3DTPS/EnemyHitMaster1.png"><br>
<img src="Image/3DTPS/EnemyHitPart.png"><br>

Unity作業<br>
1. EnemyにEnemyHitMasterをつける<br>
2. EnemyHitMasterにEnemyHitについるエフェクトのプレハブをシリアライズする<br>
3. EnemyについているEnemyHitを削除する<br>
4. TankChassis、TankTracksLeft、TankTracksRight、TankTurretにMeshColliderをつけてConvertexとIsTriggerをOnにする<br>
5. 同じものにRigitBodyをつけてUseGarvityをOffにする<br>
6. 同じものにEnemyHitPartをつける<br>

## エネミーの死亡処理を作成する
現状のエネミーはHPが0になるといきなり消える状態になっています。<br>
あまりにも唐突に消えてしまうので、HPが0になったら、バラバラになって<br>
一定時間が経ったら消える処理を入れてみましょう。<br>
EnemyHitMaster.csとEnemyAi.csを変更します。<br>
<img src="Image/3DTPS/EnemyHitMaster00.png"><br>
<img src="Image/3DTPS/EnemyHitMaster01.png"><br>
<img src="Image/3DTPS/EnemyAi_Dead0.png"><br>
<img src="Image/3DTPS/EnemyAi_Dead1.png"><br>
<img src="Image/3DTPS/EnemyAi_Dead2.png"><br>

# シーンの切り替え処理を作成する
シーンの切り替えを実装します。<br>
ゴールとシーンをフェードする処理を作成してください。<br>
SceneLoadManager.cs<br>
<img src="Image/3DTPS/SceneManager0.png"><br>
<img src="Image/3DTPS/SceneManager1.png"><br>
<img src="Image/3DTPS/SceneManager2.png"><br>
Goal.cs<br>
<img src="Image/3DTPS/Goal.png"><br>

Unity作業<br>
Canvasを新しく作成して、SceneLoadMangaerをつける<br>
Canvasの中にImageを作成して、サイズを1920：1080にする<br>
CanvasのSortOrderを32767にする<br>
Imageの位置を1920：0にする<br>
Tanksのプレハブの中にあるTemporaryInvincibilityをシーンに設置する<br>
TemporaryInvincibilityのPowerUpを削除する<br>
TemporaryInvincibilityにGoalをアタッチする<br>

# 音をつける
玉を撃った時や敵を倒した際に音がなるようにしましょう。<br>
SoundManager.csを作成してください。<br>
<img src="Image/3DTPS/SoundManager0.png"><br>
<img src="Image/3DTPS/SoundManager1.png"><br>
音を鳴らす側にも修正を入れます。<br>
EnemyAi.cs
<img src="Image/3DTPS/EnemyAi_Sound.png"><br>
TPSShooterTap.cs
<img src="Image/3DTPS/TPSShooterTap_Sound.png"><br>

Unityの作業<br>
Publicの1_27フォルダーにサウンドがあるのでダウンロード<br>
空のオブジェクトを生成して、名前をSoundManagerにする<br>
SoundManagerにSoundManager.csをアタッチする<br>
SoundManagerにAudioSorceをAddCompornentする<br>
SoundManagerにダウンロードしたサウンドをシリアライズする<br>
SoundManagerにAudioSorceをシリアライズする<br>

# サウンドが重複して再生されない問題を解決する
現在のサウンドマネージャーの設定だとサウンドが<br>
一つしか再生できないようになっています。<br>
複数のSEが同時に再生できるようにしましょう。<br>
<img src="Image/3DTPS/SoundManager_Bug.png"><br>

SoundManagerの中に空オブジェクトを作成して、AudioSorceをアタッチする<br>
それをコピーして１０個くらい作る<br>
作った１０個をSoundManagerにシリアライズする<br>