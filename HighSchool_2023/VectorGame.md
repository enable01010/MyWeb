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
\\10.80.100.100\Public\06_23年入学生用\高等部3年制ゲームプログラマー専攻23生\谷山講師\10.03データ<br>
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

## 玉の発射を制御するスクリプトを作成する
<img src="Image/HighSchool_2024/VectorDirAttack_0.png"><br>
<img src="Image/HighSchool_2024/VectorDirAttack_1.png"><br>
<img src="Image/HighSchool_2024/VectorDirAttack_2.png"><br>

## この書き方で攻撃パターンを作るとこんな感じになる
``` clike

using System.Collections;
using UnityEngine;

public class EnemyAttackManager : MonoBehaviour
{
    [SerializeField] GameObject bulletPlayerDir;
    [SerializeField] GameObject bulletRightDir;
    [SerializeField] GameObject bulletLeftDir;
    [SerializeField] GameObject bulletUpDir;
    [SerializeField] GameObject bulletDownDir;

    private void Awake()
    {
        StartCoroutine(AttackRoutine());
    }

    IEnumerator AttackRoutine()
    {
        yield return null;

        while(true)
        {
            int rand = Random.Range(1, 7);
            //　int rand = 2; // テスト用固定
            switch (rand)
            {
                case 1:
                    yield return StartCoroutine(AttackPattern_1());
                    break;
                case 2:
                    yield return StartCoroutine(AttackPattern_2());
                    break;
                case 3:
                    yield return StartCoroutine(AttackPattern_3());
                    break;
                case 4:
                    yield return StartCoroutine(AttackPattern_4());
                    break;
                case 5:
                    yield return StartCoroutine(AttackPattern_5());
                    break;
                case 6:
                    yield return StartCoroutine(AttackPattern_6());
                    break;
            }
        }
    }
     IEnumerator AttackPattern_1()
    {
        // 10発、0.2秒ごとにずつ、右と下に弾を撃つ
        for (int i = 0; i < 10; i++)
        {
            Instantiate(bulletRightDir, new Vector3(-3, 2.3f, 0), Quaternion.identity);
            Instantiate(bulletLeftDir, new Vector3(3, -2.3f, 0), Quaternion.identity);
            yield return new WaitForSeconds(0.2f);
        }

        // 発射位置を上下にずらしながら0.5秒ごとに撃つ
        for (int i = 0; i < 10; i++)
        {
            Instantiate(bulletRightDir, new Vector3(-3, 2.3f - i * 0.5f, 0), Quaternion.identity);
            Instantiate(bulletLeftDir, new Vector3(3, -2.3f + i * 0.5f, 0), Quaternion.identity);
            yield return new WaitForSeconds(0.5f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }

    IEnumerator AttackPattern_2()
    {
        // 円周を回るように弾を撃つ
        int bulletCount = 36;
        float radius = 5.0f;
        for (int i = 0; i < bulletCount * 2; i++)
        {
            float angle = i * 360.0f / bulletCount * Mathf.Deg2Rad;
            Vector3 spawnPos = new Vector3(Mathf.Cos(angle) * radius, Mathf.Sin(angle) * radius, 0);
            Instantiate(bulletPlayerDir, spawnPos, Quaternion.identity);
            yield return new WaitForSeconds(0.1f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }

    IEnumerator AttackPattern_3()
    {
        // 左側が下　、右側が上に移動する弾を撃つ
        for (int i = 0; i < 10; i++)
        {
            for (int j = 0; j < 10; j++)
            {
                Instantiate(bulletDownDir, new Vector3(-3 + j * 0.3f, 3.5f, 0), Quaternion.identity);
                Instantiate(bulletUpDir, new Vector3(3 - j * 0.3f, -3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(1f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }

    IEnumerator AttackPattern_4()
    {
        // 左側が下　、右側が上に移動する弾を撃つ
        // さらに、上下に移動する弾も追加
        for (int i = 0; i < 10; i++)
        {
            for (int j = 0; j < 10; j++)
            {
                if (i % 2 == 0)
                {
                    Instantiate(bulletDownDir, new Vector3(-3 + j * 0.3f, 3.5f, 0), Quaternion.identity);
                    Instantiate(bulletUpDir, new Vector3(3 - j * 0.3f, -3.5f, 0), Quaternion.identity);
                }
                else
                {
                    Instantiate(bulletRightDir, new Vector3(-3.5f, -3.0f + j * 0.3f, 0), Quaternion.identity);
                    Instantiate(bulletLeftDir, new Vector3(3.5f, 3.0f - j * 0.3f, 0), Quaternion.identity);
                }
            }
            yield return new WaitForSeconds(1f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }

    IEnumerator AttackPattern_5()
    {
        //　格子状に弾を撃つ
        for (int i = 0; i < 15; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.2f);
        }

        // 格子状の弾の位置を上に上げる
        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j + 0.15f * i, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.3f);
        }

        //　格子状に弾を撃つ
        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j + 1.5f, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.2f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j + 1.5f, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j + 0.15f * i, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.3f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j + 1.5f, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j + 1.5f, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.2f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j + 1.5f - 0.15f * i, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j + 1.5f, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.3f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j + 1.5f, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.2f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j + 1.5f - 0.15f * i, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.3f);
        }

        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 3)
            {
                Instantiate(bulletRightDir, new Vector3(-3.5f, 0.5f * j, 0), Quaternion.identity);
                Instantiate(bulletDownDir, new Vector3(0.5f * j, 3.5f, 0), Quaternion.identity);
            }
            yield return new WaitForSeconds(0.2f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }

    IEnumerator AttackPattern_6()
    {
        for (int i = 0; i < 10; i++)
        {
            for (int j = -5; j <= 5; j += 2)
            {
                if (i % 2 == 0)
                {
                    Instantiate(bulletPlayerDir, new Vector3(0.35f * j, 3.5f, 0), Quaternion.identity);
                }
                else
                {
                    Instantiate(bulletPlayerDir, new Vector3(0.35f * j, -3.5f, 0), Quaternion.identity);
                }
            }
            yield return new WaitForSeconds(1.0f);
        }

        // 技の終了後5秒待つ
        yield return new WaitForSeconds(5.0f);
    }
}

```
# ゲームでちょくちょく使う小物をちゃんと作る

## HPのアニメーション
<img src="Image/HighSchool_2024/HPBar.png"><br>
<img src="Image/HighSchool_2024/PlayerHit_0.png"><br>

## プレイヤーの無敵時間
<img src="Image/HighSchool_2024/PlayerHit_1.png"><br>

## プレイヤーの明滅
<img src="Image/HighSchool_2024/PlayerColor.png"><br>
<img src="Image/HighSchool_2024/PlayerHit_2.png"><br>

## ヒットストップ
<img src="Image/HighSchool_2024/HitStop.png"><br>
<img src="Image/HighSchool_2024/PlayerHit_3.png"><br>

## カメラ揺れ
<img src="Image/HighSchool_2024/CamShake.png"><br>
<img src="Image/HighSchool_2024/PlayerHit_4.png"><br>
