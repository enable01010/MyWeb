# OneButton

## Unityプロジェクト作成
<img src="Image/HighSchool_2025/OneButtonCreate.png" height="450"><br>
Unity6　Universal2Dでプロジェクトを作成してくだしさい。<br>
生成されたら、Sceneフォルダーを消してください。<br>
その後パブリックに上がってるデータすべてをAsset直下に入れてください。<br>
さらに、Edit＞Preject Setting ＞　TextMeshProの上のボタンをいれてください。

## ゲームの確認
3種類のゲームが作ってあります。<br>
すべてのゲームはエンターキーだけで動作します。<br>

### ineMove
<img src="Image/HighSchool_2024/LineMove.png" height="450"><br>
LineMoveはエンターキーを押すことで、画面下部のプレイヤーが左右に動きます。（緑の四角）<br>
上から降ってくる青色の四角をより多くとりましょう。<br>
それ以外の色は極力触れないようにしましょう。<br>
ゲームオーバーまでに取れた青色と、生き残った時間がスコアになります。<br>

### AirPlane
<img src="Image/HighSchool_2024/AirPlane.png" height="450"><br>
AirPlaneはエンターキーを押してる間上に、押してないときは下に動きます。<br>
画面の上下端に行くとゲームオーバーになります。<br>
又、飛んでくる鳥に当たってもゲームオーバーになります。<br>
できる限り長い間生き残りましょう。<br>

### CircleMove
<img src="Image/HighSchool_2024/CircleMove.png" height="450"><br>
CircleMoveはエンターキーを押し続けることでキャラクターが溜めに入ります。<br>
エンターキーを離すと溜めた量に応じて早く動きます。<br>
飛んでくる矢に当たるとゲームオーバーです。<br>
できる限り長い間生き残りましょう。<br>

## よく使うプログラミング
### 時間計測
〇秒立ったら何かをするプログラムはよく使います。<br>
比較的すぐにかけるようになっておくと便利です。<br>

~~~ clike
public class LineMoveNodeDeleter : MonoBehaviour
{
    [SerializeField] float deleteTime = 10;//　ノードを消すための時間
    float time;//現在の経過時間

    void Update()
    {
        //一定時間が経過した場合に実施
        time += Time.deltaTime;
        if(time >= deleteTime)
        {
            //　自身を破棄
            Destroy(gameObject);
        }
    }
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回は10秒立つと自分自身を廃棄するプログラム例です。（LineMoveNodeDeleter.cs）<br>
  if文の中で自身を破棄していますが、書き換えれば<br>
  ・一定時間後に攻撃<br>
  ・一定時間に１回オブジェクトを生成<br>
  ・一定時間経過でスコア追加<br>
  ・一定時間経過で難易度上昇<br>
  などいろいろなことを実装することができます。<br>
</div>


### 当たったオブジェクト判定
何かのオブジェクトに当たった際にプログラムを走らせたい事は多々あります。<br>
OnTrgger系とOnCollision系は覚えておきましょう。<br>
~~~ clike
using UnityEngine;

public class LineMoveNodeDestroy : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        //　プレイヤーに当たった際にノードを破棄
        if (collision.gameObject.name == "Player")
        {
            //　ノードを削除
            Destroy(gameObject);
        }
    }
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回はプレイヤーに当たった場合に自身を破棄するプログラムの例です。（LineMoveNodeDestroy.cs）<br>
  上と同じようにDestroyの部分を書き換えれば色々な事ができます。<br>
  また、例文のifで行っているようにcollisionからオブジェクト情報を取得して、<br>
  特定のオブジェクトだった場合のみ処理をするようなプログラムを作ることもできます。<br>
</div>


### Transformでの移動
なにも移動させずにゲームを作ることはほぼ不可能でしょう。<br>
Transformを使ったオブジェクトの移動もできるようになっておきましょう。<br>

~~~ clike
public class CircleMoveCenterMove : MonoBehaviour
{
    [SerializeField] float speed = 3.0f; // 移動速度
    Vector3 dir; // 移動方向

    private void Start()
    {
        // 中央に向けての方向と距離を取得
        Vector3 distance = Vector3.zero - transform.position;

        // 取得した方向と距離を方向だけに修正
        dir = distance.normalized;
    }

    private void Update()
    {
        // 中央に向けて移動
        Vector3 nextPos = transform.position;
        nextPos += speed * Time.deltaTime * dir;
        transform.position = nextPos;
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回は中央向きにまっすぐ進み続けるプログラムです。（CircleMoveCenterMove.cs）<br>
  Startのタイミングで移動方向の計算をして、
  Updateで計算した方向に進み続けています。
</div>

### 特定のオブジェクトを一定間隔でランダムに生成
ランダムでオブジェクトを生成できると、ゲームを繰り返して遊ぶような状況を想定する場合に便利です。<br>

~~~ clike
public class LineMoveNodeCreater : MonoBehaviour
{
    [SerializeField] GameObject[] nodes;　//　生成するノードの一覧

    [SerializeField] float createPitch;　//　ノードを生成する間隔
    float time;　//　現在の経過時間

    private void Update()
    {
        //　プレイヤーが終了していない場合のみ実施
        if (LineMovePlayer.isEnd == true) return;

        //一定時間経過した場合に実施
        time += Time.deltaTime;
        if (time >= createPitch)
        {
            //　時間リセット
            time = 0;

            // ランダムで左右を決定
            Vector3 createPos = SelectLine();

            // ランダムで生成するオブジェクトを決定
            GameObject pref = SelectNode();

            //　ノード生成
            GameObject obj = Instantiate(pref, transform);
            obj.transform.position = createPos;
        }
    }

    /// <summary>
    /// どっちのラインの位置に生成するかランダムで選択する
    /// </summary>
    /// <returns>抽選された位置</returns>
    private Vector3 SelectLine()
    {
        //　ランダムで左右を取得　0→左　：　1→右
        int posRand = Random.Range(0, 2);

        //　ランダムで取得した数字に合わせて位置座標を生成
        Vector3 pos = Vector3.zero;
        Transform parent = null;
        if (posRand == 0)
        {
            // 左側
            pos = new Vector3(-3, 7, 0);
        }
        else
        {
            // 右側
            pos = new Vector3(3, 7, 0);
        }

        return pos;
    }

    /// <summary>
    /// どのノードを生成するかランダムで選択する
    /// </summary>
    /// <returns>抽選されたノード</returns>
    private GameObject SelectNode()
    {
        //　ランダムでノードを選出
        int random = Random.Range(0,nodes.Length);
        return nodes[random];
    }

}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回のは配列内のオブジェクトをランダムで、どっちらかの列に、一定間隔で生成するプログラムです。（LineMoveNodeCreater.cs）<br>
　先ほども出てきた、時間計測のプログラムを使いつつ、ランダム位置の生成、ランダムでプレハブの決定を駆使して作成します。<br>
</div>

### ガード節
プログラムでif文だらけになって見にくい状態になるのを防ぐ際に使います。<br>
例えばプレイヤーが死んでいなかったらなど、Ｕｐｄａｔｅ全体を回さない場合などに使うと便利です。<br>

~~~ clike
public class CircleMoveScoreManager : MonoBehaviour
{
    //　コンポーネント
    TextMeshProUGUI tmp;
    int score;//スコア
    [SerializeField] float scoreUpTime = 1.0f;//スコアが上がる間隔
    float time = 0;//経過時間

    private void Awake()
    {
        // コンポーネント取得
        tmp = GetComponent<TextMeshProUGUI>();
    }

    private void Update()
    {
        // プレイヤーが終了している場合は処理しない
        if (CircleMovePlayer.isEnd == true) return;

        // 一定時間経過で処理
        time += Time.deltaTime;
        if(time > scoreUpTime)
        {
            //　タイムリセット
            time = 0;

            //　タイム追加
            score++;
        }
        
        //　スコア表示リセット
        tmp.text = "score:" + score;
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回のはプレイヤーが生きてる限り時間を計測して、スコアを上げていくプログラムです。（CircleMoveScoreManager.cs）<br>
　プレイヤーが死んでいると一番上のif文でスクリプトが終了して、<br>
　プログラムが動作しないようになっています。
</div>

### Updateを止める
1回だけ起動したいようなプログラムを実施したい場合が多々あります。
そういった際に便利です。
~~~ clike
public class LineMoveLineSwitch : MonoBehaviour
{
    [SerializeField] float switchTime = 3;　//　左右入れ替わるまでの時間
    float time; // 経過時間

    private void Update()
    {
        //　一定時間が経過したら実行
        time += Time.deltaTime;
        if(time >= switchTime)
        {   
            //　左右を入れ替える
            Vector3 nextPos = transform.position;
            nextPos.x *= -1;
            transform.position = nextPos;

            // プログラムを止める
            this.enabled = false;
        }
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  今回はLineMoveの左右を一定時間後に入れ替えるプログラムです。（LineMoveLineSwitch.cs）<br>
  左右を１回だけ入れ替えてほしいですが、１回動作したらそれ以降動かないでほしい場合に、
  enableをfalseにすることでプログラムのUpdateを止めると便利です。
</div>

##　みんなで作ってみよう
CircleMoveでまっすぐ進む矢以外のオブジェクトを作成してみましょう。<br>
・早い矢、遅い矢<br>
・一定量進んだら折り返す<br>
<!--
~~~ clike
public class CircleMoveReturnMove : MonoBehaviour
{

    [SerializeField] float returnTime = 3.0f;
    float time; //　経過時間

    CircleMoveCenterMove move;

    private void Awake()
    {
        move = GetComponent<CircleMoveCenterMove>();
    }

    private void Update()
    {
        time += Time.deltaTime;
        if (time > returnTime)
        {
            move.dir *= -1;

            Vector3 angle = transform.eulerAngles;
            angle.z += 180;
            transform.eulerAngles = angle;

            enabled = false;
        }
    }
}
~~~
-->

・触っても死なない、得点UP<br>
<!--
~~~ clike
public class CircleMoveScoreUp : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if(collision.gameObject.name =="Player")
        {
            CircleMoveScoreManager.score++;
        }
    }
}
~~~

~~~ clike
public class CircleMoveHitArrowDestroy : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.gameObject.name == "Player")
        {
            Destroy(gameObject);
        }
    }
}
~~~
-->

+CircleMoveScoreManagerのint scoreをpublic static int scoreに変更<br><br>
・内側から動く矢<br>