# 前期の復習※if文

## プロジェクトの立ち上げ
<img src="Image/HighSchool_2025/OneButtonCreate.png" height="450"><br>
Unity6で2Dプロジェクト、名前をOneButtonにしてプロジェクトを作成してください。<br>
<br>
<br>
立ち上がったら、Publicに入っている8/26のデータをAsset直下に入れてください<br>
Asset<br>
-Data<br>
-LineMove<br>
-Scene（元のやつは消してください）<br>

## 実際にプレイしてみる
画面上からノードが降ってきます。<br>
緑が自分でエンターキーを押すことで左右を移動することができます。<br>
青色のノードを拾うとスコアが上がります。<br>
実際にプレイしてみましょう。<br>

## if文の使用例
### ボタンが押された際に何かをする
~~~ clike
using UnityEngine;

[RequireComponent(typeof(Animator))]
[RequireComponent(typeof(BoxCollider2D))]
[RequireComponent(typeof(Rigidbody2D))]
public class Player : MonoBehaviour
{
    Animator anim;
    private void Awake()
    {
        anim = GetComponent<Animator>();
    }

    // Update is called once per frame
    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Return))
        {
            anim.SetTrigger("Move");
        }
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  Updateの中にif文を書きInput系を使うことで入力検知を行うことができます。<br>
  今回のプレイヤーのスクリプトではEnterキー（Return）を押すことで、アニメーションが作動し、左右の位置が入れ替わります。
</div>

### 特定のオブジェクトに触れた際に何かをする
~~~ clike
using UnityEngine;

public class HitOut : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if(collision.gameObject.name == "Player")
        {
            Destroy(collision.gameObject);
        }
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  OnTriggerEnter等のオブジェクトが当たった際に呼ばれる関数内で、<br>
  Collisonを使うことで特定のオブジェクトに当たったことを検知することができます。
</div>

### 一定期間で何かを行う
~~~ clike
using UnityEngine;

public class NodeCreater : MonoBehaviour
{
    [SerializeField] float createPitch = 1.0f;
    float nowTime;

    //　※関係ないので割愛

    private void Update()
    {
        nowTime += Time.deltaTime;
        if(nowTime >= createPitch)
        {
            nowTime = 0;

            //　※関係ないので割愛
        }
    }


}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  上記のようなプログラムを組むことで１秒（createPitch）に1回の処理をすることができます。
</div>

### ランダムで何かを行う
~~~ clike
// ランダムで左右どちらにするか選択
    int randomPos = Random.Range(0, 2);
    Vector3 pos = new Vector3(0, 7, 0);
    switch (randomPos)
    {
        case 0:
            pos.x = -3;
            break;
        case 1:
            pos.x = 3;
            break;
    }


    // ランダムでどのオブジェクトを生成するか選択
    int randomObj = Random.Range(0, createObjCount);
    GameObject pref = null;
    switch(randomObj)
    {
        case 0:
            pref = node;
            break;
        case 1:
            pref = scoreUp;
            break;
    }

    // オブジェクト生成
    GameObject obj = Instantiate(pref, transform);
    obj.transform.position = pos;
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  上記のようにRandomとif文Swith文を組み合わせることで、ランダムな挙動を作成することができます。
</div>


## 問題
### ①　時間経過でスピードが上がるようにしましょう。
５秒経過するごとにゲームの速度が1.1倍になるSpeedUp.csを作成し、Lineにアタッチしましょう。

### ②　一定時間が立つと左右が入れ替わるオブジェクトを作成しましょう。
出てきてから2秒立つと左右が入れ替わるオブジェクトLineMove.csを作成し、<br>
プレハブを作成しましょう。<br>
プレハブの作りかたは解説します。

### ③　一定時間が立つと透明になるオブジェクトを作成しましょう。
出てきてから1秒立つと透明になるオブジェクトBlind.csを作成し<br>
それ用のプレハブを作成しましょう。<br>