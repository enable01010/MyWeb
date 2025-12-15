# 授業目的
みなさんが書いたプログラムをみると、<br>
main()の中に上から順番にずらっとコードが並んでいる事が多いです。<br>

正直C,B問題くらいまでならこっちの方が理解しやすい場合も多いでが、<br>
回答までの工程が複雑になるにつれて、人が読めたもんじゃないコードになっていきます。<br>

そこで、クラスを使ったプログラムしやすいやり方を学びます。<br>

# パイザでクラスを使うメリット
・コードの使い回し<br>
・問題解決の手順化<br>


# コードの使いまわし

皆さん、パイザ解いている時にVector2とか使いたくなりませんか？<br>
２次元配列の座標を扱う時にint x,y;みないなコード書いてませんか？<br>

こういう物は先にクラスとして作って置いて、パイザ開始時にコピペして使うと楽です<br>
例えば、こんな感じでVector2クラスを作っておきます。<br>
~~~ clike
    /// <summary>
    /// パイザ用コピペVector2（int）
    /// </summary>
    public class Vector2
    {
        static public readonly Vector2 zero = new Vector2(0, 0);
        static public readonly Vector2 right = new Vector2(1, 0);
        static public readonly Vector2 left = new Vector2(-1, 0);
        static public readonly Vector2 up = new Vector2(0, 1);
        static public readonly Vector2 down = new Vector2(0, -1);

        public int x;
        public int y;

        public Vector2(int x, int y)
        {
            this.x = x;
            this.y = y;
        }

        public static Vector2 operator +(Vector2 a, Vector2 b)
        {
            return new Vector2(a.x + b.x, a.y + b.y);
        }
        
        public static Vector2 operator -(Vector2 a, Vector2 b)
        {
            return new Vector2(a.x - b.x, a.y - b.y);
        }
    }
~~~


パイザを解いていて、この処理別の問題で書いた事あるなーって思うことありませんか？<br>
例えば、2次元配列の入力受け取り、出力とか、不定な長さの配列の受け取りとか<br>
そういうのを毎回一から書いていると、時間がかかりますし、ミスも増えます。<br>
なので、入力用のクラスを作ってそこにまとめて置くとらくです。<br>

# 問題解決の手順化
僕がパイザを解くときのパターンは大きく２つです。<br>
<br>
1.<br>
入力受け取り<br>
処理<br>
出力<br>
<br>
2.<br>
入力受け取り<br>
while(　終了検知　）<br>
{<br>
	処理<br>
}<br>
出力<br>
<br>
他にも状況により変わったりしますが、大体このパターンに当てはまります。<br>

これをクラスにしておくと、今自分が何を考えなければいけないのかが明確になりやすいです。<br>
(例）<br>
~~~ clike

public class Manager
{
	// 入力受け取り
	public void Init()
	{
	}

    // 処理
	public void Update()
	{
	}

    // 出力
	public void Output()
	{
	}
}

main()
{
    Manager manager = new Manager();
    manager.Init();
    manager.Update();
    manager.Output();
}
~~~

~~~ clike

public class Manager
{
	// 入力受け取り
	public void Init()
	{
	}

    // 処理
	public void Update()
	{
	}

    // 繰り返し終了判定
    public bool GetIsEnd()
    {
    }

    // 出力
	public void Output()
	{
	}
}

main()
{
    Manager manager = new Manager();
    manager.Init();

    while(!manager.GetIsEnd())
    {
        manager.Update();
    }

    manager.Output();
}
~~~
そのうえで、僕は入力受け取り→出力→処理の順でコードを書く場合が多いです。<br>
この順番でやると、処理を書く際にどんなデータを元に、何に変換したら良いかが明確になるからです。<br>

