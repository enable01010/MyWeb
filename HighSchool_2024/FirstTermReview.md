# 前期の復習
## プログラム基礎知識
### 条件分岐
if文、switch文などの条件によって処理を分ける方法があります。<br>
~~~ clike
if(条件式)
{
	//条件式がtrueのときに実行される
}
else if(別の条件式)
{
	//別の条件式がtrueのときに実行される
}
else
{
	//上記のどれにも当てはまらないときに実行される
}
~~~
~~~ clike
switch(変数)
{
	case 値1:
		//変数が値1のときに実行される
		break;
	case 値2:
		//変数が値2のときに実行される
		break;
	default:
		//上記のどれにも当てはまらないときに実行される
		break;
}
~~~
### 繰り返し
for文、while文などの繰り返し処理を行う方法があります。<br>
~~~ clike
for(int i = 0; i < 繰り返す回数; i++)
{
	//繰り返し処理
}
~~~
~~~ clike
while(条件式)
{
	//条件式がtrueの間繰り返し処理
}
~~~

### 配列
配列は複数のデータをまとめて扱うためのデータ構造です。<br>
~~~ clike
	int[] numbers = new int[5]; // 整数型の配列を5つ分用意
	numbers[0] = 10; // 配列の1番目に10を代入
	numbers[1] = 20; // 配列の2番目に20を代入
	numbers[2] = 30; // 配列の3番目に30を代入
	numbers[3] = 40; // 配列の4番目に40を代入
	numbers[4] = 50; // 配列の5番目に50を代入
	int sum = 0; // 合計値を格納する変数
	for(int i = 0; i < numbers.Length; i++) // 配列の長さ分繰り返し
	{
		sum += numbers[i]; // 各要素を合計値に加算
	}
	Console.WriteLine("合計値: " + sum); // 合計値を表示
~~~
### 関数
関数は特定の処理をまとめて再利用可能にするための仕組みです。<br>
~~~ clike
void Greet(string name)
{
	Console.WriteLine("Hello, " + name + "!");
}

void Start()
{
	Greet("Alice"); // "Hello, Alice!" と表示
	Greet("Bob");   // "Hello, Bob!" と表示
}

~~~
### オブジェクト指向
オブジェクト指向は、データとその操作を一つの単位（オブジェクト）として扱う考え方です。<br>
~~~ clike
class Car:Monobehaviour
{
	public string color; // 車の色
	public int speed;    // 車の速度
	public void Drive() // 車を運転するメソッド
	{
		Console.WriteLine("The " + color + " car is driving at " + speed + " km/h.");
	}
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  オブジェクト指向についてはそんな考え方があるんだなと覚えておく程度で大丈夫です。<br>
  Unityを使っていたらいやでもこの書き方になります。<br>
  ただITや別のツールを使ってゲームを制作する時に出てくる可能性があります。<br>
  その時は、Unityみたいにオブジェクト単位でスクリプト作るんだな～と雰囲気がわかると良いです。
</div>

## パイザ
### 標準入力・標準出力
パイザで標準入力を使って、パイザのデータを受け取り、標準出力で結果を出力します。<br>
~~~ clike
using System;
class Program
{
	static void Main()
	{
		// 標準入力から1行読み込み
		string input = Console.ReadLine();
		
		// 入力された文字列を整数に変換
		int number = int.Parse(input);
		
		// 整数を2倍にして標準出力に表示
		Console.WriteLine(number * 2);
	}
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  Console.ReadLine() →　標準入力<br>
  Console.WriteLine() →　標準出力<br>
  この標準入力・標準出力は書き方こそ違いますが、他の言語や開発環境でも存在します。<br>
  例えばUnityではInput.GetKey○○やDebug.Log()などです。<br>
</div>

### 便利な関数<Linq>
C＃やパイソンなどで使えるLinqという便利な関数群があります。<br>
~~~ clike
using System;
using System.Linq;
class Program
{
	static void Main()
	{
		// 標準入力から1行読み込み
		string input = Console.ReadLine();
		
		// 入力された文字列をスペースで分割して整数の配列に変換
		int[] numbers = input.Split(' ').Select(int.Parse).ToArray();
		
		// 配列の要素を昇順にソート
		Array.Sort(numbers);
		
		// ソートされた配列を標準出力に表示
		Console.WriteLine(string.Join(" ", numbers));
	}
}
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  具体例として、Linqでよく使う関数をいくつか紹介します。<br>
  Select() → 配列の各要素に対して指定した関数を適用します。<br>
  Where() → 配列の各要素に対して指定した条件を満たす要素だけを抽出します。<br>
  Count() → 配列の要素数を取得します。<br>
  Sum() → 配列の要素の合計を計算します。<br>
  Max() → 配列の要素の最大値を取得します。<br>
  Min() → 配列の要素の最小値を取得します。<br>
  OrderBy() → 配列の要素を昇順にソートします。<br>
  OrderByDescending() → 配列の要素を降順にソートします。<br>
  こんな感じのがあったと覚えておくと、パイザで必要になった時に、調べて使えるようになります。
</div>

## Unity
### よく使う処理
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


## 就活に向けて
就活は皆さんが、初めて自分から動く必要になる出来事だと思います。<br>
いままで、小学校、中学校、バンタンと成り行き、社会の仕組みに沿って、人が用意してくれた道を進んで来たと思います。<br>
しかし、就活は自分で準備して、自分で動いて、自分で進む初めての出来事になります。<br>
そんな、初めてを踏み出すみなさんに、僕の失敗談を少し伝えようかなと思います。<br>

### 就活の開始時期
担当直入にいうとベストは10月位にどこかしらに応募する。<br>

スケジュールを組むときは大抵逆算から入ります。<br>

<br>
例年、4月位から内定の打ち止めが始まります。<br>
→ 3月位には最終面接<br>
→ 2月位には本命の応募<br>
→ 12月位にはたくさん応募して面接や書類作成の練習したい<br>
→ 10月位には１～２件応募してみて、どんな準備が必要か体験したい<br>

<br>
4月を超えるとどうなってくるか、、、
→　応募したい企業の募集が終わっている<br>
→　企業もある程度採用が決まって、残りはイイ人が要れば取るけど、<br>
    無理に取らなくていいやってなる

### ポートフォリオ
正直、何が良くて何が悪いなんて事は人に寄ります。個性と感じ方です。<br>
なんで、いろんな人に見てもらいましょう。<br>
メイチさん、マツガミさん、その他プログラムの先生、松岡先生。<br>
いろんな人からアドバイスをもらって、取り入れたいものだけ取り入れましょう。<br>

Q&A　アドバイスもらったけど、自分の意見のが正しいと思います！<br>
正直、こいつ何言ってんだと思う事もあります。そういう意見は切り捨てましょう。<br>
講師も自分の意見が全員に当てはまるとは思っていません。<br>
自分の意見が完璧ならみんな就活成功するもん。<br>
<br>
Q&A スタッフや講師が忙しそうです！<br>
うるさい仕事しろ！。<br>
僕を初めとしたバンタンにいる大人は、みんなからお金をもらってる仕事してるんで、<br>
気兼ね無く頼ったら良いです。<br>
<br>
Q&A バンタンから就活の案内全然来ないからまだじゃないん大丈夫ですか？<br>
大丈夫じゃないです。<br>
バンタンからの案内はとにかく遅いです。<br>
下手したら、ゲーム外車じゃなくて、工場系の内定確約系すべりどめ求人が先に来るぐらいです。<br>
就活は自分たちで進んでいくものです。<br>