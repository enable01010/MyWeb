# リズムゲーム

## 目的
前回の授業で、作成してあるリズムゲームのある程度の機能には触れていただいたと思います。<br>
今回はそのプロジェクトの解析を通じて、プログラムの設計や、書き方のパターンを身に着けて貰えればと思います。<br>

# よく使うプログラム
## コルーチン
今回のプロジェクトではコルーチンを多めに使用しています。<br>
改めて書き方と使い方を覚えましょう。<br>
~~~ clike

private void Awake()
{
	// Move()コルーチンの開始
	StartCorutine(Move());
}

// Move()コルーチンの実部
private IEnumrator Move()
{
	yield return null;

	/*割愛*/
}

~~~
コルーチンは特定の終了を待ってから実施したり、一定の秒数かけて処理する際に使われます。<br>
・10秒間右に移動する<br>
・アニメーションが終わってから、シーン遷移する<br>
<br>
今回のプロジェクトでは移動のために使う事が多かったです。<br>

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 補足：</strong><br>
  yield return null; →　１フレーム待つ
  yield return new WaitForSeconds(1.0f);　→　1秒待つ
  yield return StartCorutine(Move());　→　Move()コルーチンが終わるまで待つ
</div>

<br>

また今回のプロジェクトではありませんが、コルーチンを最も活かした書き方は下のような書き方になります。<br>

~~~ clike

private IEnumrator SceneLoadRoutine()
{
	yield return StartCorutine(FadeOut());
	yield return StartCorutine(LoadScene());
	yield reutrn StartCorutine(FadeIn());
}

private IEnumrator FadeOut()
{
	// フェードアウトする処理（割愛）
}

private IEnumrator LoadScene()
{
	// シーンをロードする処理（割愛）
}

private IEnumrator FadeIn()
{
	// フェードインする処理（割愛）
}

~~~
このような書き方をする事で、<br>
→フェードアウト開始<br>
→フェードアウトが完了したら、シーンロード<br>
→シーンのロードが完了したらフェードイン<br>
みたいな順番を守ったコードを書くことができます。<br>

## アクション・ファンクション
Action（アクション）・Function（ファンクション）は関数を変数にいれるようなイメージです。<br>
例えば<br>
・整数の変数がint<br>
・文字列の変数がstring<br>
のようなイメージで<br>
・関数の変数がAction・Functionになります。<br>

よく使う使い方は、通知を受け取る際に使います。<br>
今回のプロジェクトでは、ピッチ（リズム１回）をシーン上のオブジェクトに通知しています。<br>

~~~clike
///
///　リズムを作成するクラス
///
public class Rhythm
{
	static public List<Action> actions = new List<Action>();
	float time = 0;

	private void Update()
	{
		time += Time.deltaTime;
		if(time > 0.5f)
		{
			time = 0;

			foreach(var action in actions)
			{
				action.Invoke();
			}
		}
		
	}
}

///
///　矢のクラス
///
public class ArrowMove
{
	private void Awake()
	{
		Rhythm.actions.Add(MoveStart);// 左MoveStartの()は無し
	}

	private void MoveStart()
	{
		StartRoutine(Move()):
	}

	private IEnumrator Move()
	{
		// 移動処理（割愛）
	}
}


~~~

実は皆さんこのAction・Functionをすでに使った事があります。<br>
Unityで最も目にするのはButtonです。ボタンのコンポーネントにOnClick()みたいなやつがあって、<br>
ボタンが押されたときにこの関数呼び出してね！みたいな登録をしたことがあると思います。<br>
あれがActionです。<br>

## シングルトンパターン
まずシングルトンパターンの前に前提として、デザインパターンを紹介します。<br>

### デザインパターンとは
デザインパターンとは、プログラムでよく使う典型例みたいのものの事です。<br>
皆さんもプレイヤーの入力受取だったらこう書くよね、シーンの遷移だったらこう書くよね、<br>
みたいなプログラムの典型、みたいなのがなんとなくあると思います。<br>
それの超すごい版です。<br>

### デザインパターンの目的
・再利用性の向上<br>
・柔軟性と拡張性の向上<br>
・共通の語彙の提供<br>
・設計スキル向上<br>

余談：<br>
ダニング＝クルーガー効果の頂点はデザインパターン<br>

### よく使うデザインパターン
・Singletonパターン　（マネージャークラス）<br>
・Stateパターン　（Player系のキャラクタークラス）<br>
・ObjectPoolパターン（量産系のオブジェクト）<br>
・Observer,Eventパターン<br>
・Commandパターン<br>

## シングルトンパターンとは
シングルの名の通り、一つであることを確約することを目的としたデザインパターンです。<br>
一つであることを確約すると何がいいか<br>
→ データの重複の防止<br>
→ アクセスの簡易化、高速化<br>

<div style="border-left: 5px solid #e67e22; background: #fff3e0; padding: 0.8em; margin: 1em 0;">
  <strong>⚠️ 警告：</strong><br>
  稀に、アクセスの簡易化にシングルトンにしているプログラムを見かけますが、基本NG行動です。<br>
  簡単すぎるアクセスはバグのもとになる事が多く、現場での開発では使えません。もちろん就活でも<br>
  一つである事を確約する目的のパターンであることを忘れないようにしましょう。<br>
</div>

## 代表的なシングルトンパターンの書き方

~~~ clike

public class GameManager : MonoBehaviour
{
	public static GameManager instance;

	private void Awake()
	{
		if(instance == null)
		{
			// すでに生成されていなければ自分を登録
			instance = this;
		}
		else
		{
			// すでに生成されている場合は自身を破棄
			Destroy(gameObject);
			Debug.LogError("シングルトンとして破綻しています。");
		}
	}

	private void OnDestroy()
    {
        if (instance == this)
        {
            instance = null;
        }
    }

	public void Clear()
	{
		// クリア処理（割愛）
	}
}

public class Player:MonoBehaviour
{
	private void Update()
	{
		GameManager.instance.Clear();
	}
}

~~~

## Unityでシングルトンパターンを使う際の注意点
① instanceが無い瞬間をなくしましょう。<br>
特に複数人で作業する際に注意するべきですが、<br>
シングルトンである時点でいつでもあるものとしてコーディングする事が多いです。<br>
<br>
PlayerからSoundManagerのinstanceを呼び出したら、エラー吐くシーンと吐かないシーンがあるみたいな状況をよく見かけます。<br>
<br>
② シングルトンを破棄するな<br>
一つしか無いものをわざわざ破棄する必要が無い場合が多いです。<br>
例えばシーンの切り替わりで破棄される、破棄する必要がある、場合はそもそもシングルトンが適していない場合が多いです。<br>

## Unityでシングルトンパターンを使う際のオススメ
注意点を踏まえたうえで、シングルトンを使う際のオススメの使い方を紹介します。<br>
~~~ clike

public class GameManager : MonoBehaviour
{
	public static GameManager instance;

	// ゲーム開始時に実施
	[RuntimeInitializeOnLoadMethod]
	static void Init()
	{
		// シングルトンが必要になるオブジェクトを生成する
		GameObject obj = new GameObject("GameManager");

		// コンポーネントを追加
		instance = obj.AddCommprnent<GameManager>();

		// シーンロードで破棄しないように設定
		DontDestroyOnLoad(obj);
	}

	public void Clear()
	{
		// クリア処理（割愛）
	}
}

~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 補足：</strong><br>
  IT,ゲーム系の就活においてシングルトンをアピールする場合は、<br>
  生成を1回しか通さない点と破棄しない点を意識する事が大切と考えます。<br>
  間違っても、アクセスがやりやすくなるからシングルトンにしました！となってはいけません。<br>
  辛口ですが、最早使い方が分からないよりバッドイメージです。<br>
  シングルトンの目的は、【一つであることを確約する】であることを忘れないようにしましょう。<br>
</div>

<br>

# 実際のプログラムの解説
## リズムの検知
リズムの大元はRhythmManagerで作成しています。<br>
先ほど紹介したAction・Functionとシングルトンパターンを使っています。<br>

~~~ clike
public class RhythmManager : MonoBehaviour
{
    // シングルトン用インスタンス
    public static RhythmManager instance;

    // リズムのピッチ
    [SerializeField] float createPitch = 0.5f;
    float nowTime;

    // アクション通知用のリスト
    private List<Action> actions = new List<Action>();

    // リズムの計測を止める用フラグ
    bool isStop = false;

    private void Awake()
    {
        //　シングルトンの設定
        if (instance == null)
        {
            instance = this;
        }
        else
        {
            Destroy(gameObject);
        }
    }

    private void OnDestroy()
    {
        // 破棄する際に一緒に破棄
        if (instance == this)
        {
            instance = null;
        }
    }

    void Update()
    {
        if (isStop == true) return;

        // 時間計測して、CreatePitch秒に1回中身を実施
        nowTime += Time.unscaledDeltaTime;
        if (nowTime > createPitch)
        {
            nowTime = 0;

            //　登録されているアクションをすべて実施
            foreach(var action in actions)
            {
                action.Invoke();
            }
        }
    }

    public void SetAction(Action action)
    {
        actions.Add(action);
    }

    public void RemoveAction(Action action)
    {
        actions.Remove(action);
    }

    public void Stop()
    {
        instance.isStop = true;
    }
}
~~~

特に大事な事として、リズムをとる系のゲームでは絶対に個々のオブジェクトでリズムを計測してはいけません。<br>
オブジェクト生成のタイミングによってリズムがズレたりするので、必ず一箇所でやりましょう。<br>
また、アニメーションのループにも気をつけましょう。Time.deltaTimeによって丸められる軽微なズレが<br>
数百、数千回やると問題になります。<br>

## リズムの作成
このスクリプトは、通知を受け取る側のお手本のようなスクリプトです。<br>
通知を受け取ったら、ノードを作成するだけです。<br>
~~~ clike
public class RhythmMaker : MonoBehaviour
{
    [SerializeField] GameObject nodePref;

    private void Start()
    {
        // リズムマネージャーから通知を受け取るように登録
        RhythmManager.instance.SetAction(MakeNode);
    }

    /// <summary>
    /// ノードの作成
    /// </summary>
    private void MakeNode()
    {
        // 子階層にノードを生成
        Instantiate(nodePref, transform);
    }
}
~~~
これくらいの処理なら、さっきのRhythmManagerで作ったらいいのでは？と思う方もいると思います。<br>
半分正解で、半分不正解です。<br>
<br>
僕のプログラムは、単一責任にかなり比重を高く考えています。（説明しやすいから）<br>
プログラムを極端に軽量化、統一化したい場合はできる限りRhythmManagerに書くこともあるかもしれません。<br>
<br>
これは個人的な考えですが、学生制作や個人制作では、１ページで収まるぐらいのクラス、関数にしたほうが<br>
いいと思います。<br>

## リズムの受取
リズムの受取は概ねコライダーを使っています。<br>
・範囲の大きい失敗判定用のコライダー<br>
・範囲が中位のNormal判定用のコライダー<br>
・範囲が小さいGool判定用のコライダー<br>

~~~ clike
public class RhythmChecker : MonoBehaviour
{
    public static RhythmChecker instance;

    [SerializeField] RhythmNodeSenser senser1;
    [SerializeField] RhythmNodeSenser senser2;
    [SerializeField] RhythmNodeSenser senser3;

    private void Awake()
    {
        if (instance == null)
        {
            instance = this;
        }
        else
        {
            Destroy(gameObject);
        }
    }

    private void OnDestroy()
    {
        if (instance == this)
        {
            instance = null;
        }
    }

    /// <summary>
    /// ノードの判定
    /// </summary>
    /// <returns>判定結果</returns>
    public TimingResult GetTimingResult()
    {
        // 現状拾ってるノード
        RhythmNode senser3Node = senser3.GetNode();
        RhythmNode senser2Node = senser2.GetNode();
        RhythmNode senser1Node = senser1.GetNode();

        // ノードの判定
        RhythmNode nearNode = null;
        TimingResult result = TimingResult.Miss;
        if(senser3Node != null)
        {
            nearNode = senser3Node;
            result = TimingResult.Excellent;
        }
        else if (senser2Node != null)
        {
            nearNode = senser2Node;
            result = TimingResult.Normal;
        }
        else if (senser1Node != null)
        {
            nearNode = senser1Node;
            result = TimingResult.Miss;
        }

        // ノード破棄
        if(nearNode != null)
        {
            Destroy(nearNode.gameObject);
        }
        
        // 判定結果
        return result;
    }
}

public enum TimingResult
{
    Miss,
    Normal,
    Excellent,
}

public class PlayerMove : MonoBehaviour
{
    void Update()
    {
        // 入力チェック
        Vector2 moveDir = InputCheck();
        
        // ノードの確認
        if(moveDir.sqrMagnitude > 0)
        {
           TimingResult timingResult = RhythmChecker.instance.GetTimingResult();
            
           switch(timingResult)
            {
                case TimingResult.Miss:
                    anim.Play("MISS");
                    return;
                case TimingResult.Excellent:
                    anim.Play("GOOD");
                    StartCoroutine(MoveRoutine(moveDir));
                    break;
                case TimingResult.Normal:
                    anim.Play("SAFE");
                    StartCoroutine(MoveRoutine(moveDir));
                    break;
            }
        }
    }
}
~~~
## 時間をかけた移動
コルーチンを使った一定時間での移動方法です。<br>

~~~clike

public class Arrow : MonoBehaviour
{
    [SerializeField] Vector3 dir;
    [SerializeField] float moveTime = 0.2f;
    [SerializeField] int maxMove = 20;
    int count;

    void Start()
    {
        dir.z = 0;
        RhythmManager.instance.SetAction(Act);
    }

    private void OnDestroy()
    {
        if (RhythmManager.instance == null) return;

        RhythmManager.instance.RemoveAction(Act);
    }

    /// <summary>
    /// 時間経過時の処理
    /// </summary>
    void Act()
    {
        StartCoroutine(Move());
    }

    IEnumerator Move()
    {
        count++;
        if(count == maxMove)
        {
            Destroy(gameObject);
            yield break;
        }

        yield return new WaitForSeconds(0.25f);

        float time = 0;
        Vector3 startPos = transform.position;
        Vector3 goalPos = transform.position + dir;
        while (time < moveTime)
        {
            time += Time.deltaTime;

            float rate = time / moveTime;
            transform.position = Vector3.Lerp(startPos, goalPos, rate);

            yield return null;
        }

        transform.position = goalPos;
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        // プレイヤーにあたった場合
        if (collision.TryGetComponent<PlayerHit>(out var player))
        {
            // 死亡処理
            player.Deth();
        }
    }

~~~

## ループしてるようなアニメーターの再生
AnimationClipのループに頼らないループのような処理です。
~~~clike

public class RhythmNodeAnimator : MonoBehaviour
{
    [SerializeField] Animator anim;

    private void Start()
    {
        RhythmManager.instance.SetAction(PlayAnim);
    }

    private void PlayAnim()
    {
        anim.Play("Play");
    }
}

~~~

# プログラムの問題点・改善点を考えてみよう
<!-- 
    シングルトンではなくシリアライズでいい。
    Arrowが単一責任ではない。→プレイヤーにあったた処理、自身を廃棄する処理
    Arrowにマジックナンバー
-->