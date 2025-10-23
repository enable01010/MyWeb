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


## シングルトンパターン

# 実際のプログラムの解説
## リズムの生成
## リズムの検知
## リズムの受取
## 時間をかけた移動

# プログラムの改善点を考えてみよう