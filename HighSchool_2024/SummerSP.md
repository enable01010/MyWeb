# 夏期講習（前期復習）

## プログラムの基本
プログラムは大きく　変数、条件分岐、関数の３つで構成されています。<br>
これらをこの３要素を組み合わせる事でほとんどのものを作成する事ができます。<br>

### 変数
変数はデータの保存を行う事ができます。<br>
この変数にキャラクターのHPや、位置情報などを保存しておく事で、<br>
ゲームに必要なデータを用意します。<br>
```clike
	public class Player:MonoBehaviour
	{
		int hp; // ←これが変数

		void Start()
		{
			Debug.Log("HP:" + hp);
		}
	}
```
<br>
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 注意：</strong><br>
  一般的には変数の作りすぎは良くないです。<br>
  変数の数だけPCの要求スペックが高く、ゲームが重くなります。<br>
  また変数名（変数の名前）には意味のあるものを付けましょう。<br>
  int a;int b;などアルファベット順で変数を作成するプログラムを見かけますが、何書いてあるのかわかりません。<br>
  就活作品などでプログラムの中身まで見られる場合は見てもらえなくなるので、特に注意しましょう。<br>
</div>


### 条件分岐
条件分岐は、特定の【条件】によって処理を切り替える事ができます。<br>
例えば、”スペースキーを押している時にジャンプする”など、<br>
〇〇している時にＸＸする。などの際にif文を使ったり、<br>
”敵の数だけ、攻撃する”などの際にfor文を使ったりします。<br>
```clike
	public class Player:MonoBehaviour
	{
		int hp; 

		void Start()
		{
			if(hp < 0) // ←これが条件分岐
			{
				Debug.Log("死んだ");
			}
			else
			{
				Debug.Log("生きた");
			}

			int count = 5;
			for(int i = 0; i < count; i++)　// これが繰り返し
			{
				Debug.Log("繰り返し" + i + "回目");
			}
		}
	}
```

###	関数
関数は一つの動作をまとめた処理を実装する事ができます。<br>
関数を利用する事で同じような処理を何度も書く必要をなくす事ができます。<br>
また、公式が出している関数を使う事で、バグが少なくなり、<br>
作業時間も短縮する事ができます。<br>
Unityでよく使うRigidbody.AddForce()などがそれに該当します。<br>
こういった、別の企業さんなどが用意してくれている関数の事をAPI<br>
（アプリケーションインターフェースと言います）<br>
又、ここが一番重要なのですが、<br>
Unityでは、この関数を作る事で特定のタイミングで処理を実行する事ができます。<br>
```clike
	public class Player:MonoBehaviour
	{
		int hp; 

		void Start()// ←これが関数（オブジェクトの生成直後）
		{
			Debug.Log("HP:" + hp);
		}

		void Update()// 毎フレーム

		void OnTriggerEnter(Collider col)// オブジェクトが何かしらに触れた時
		{
			Debug.Log(col.gameobject.name);
		}
	}
```
<br>
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 注意：</strong><br>
  よく関数の中身がとてつもなく長くなっている処理を見かけます。<br>
　関数内の処理はスクロールせずに見切れるぐらいの量にしましょう。<br>
　特にUpdateの内の処理が大量になり、Updateの中に１００行ぐらい書かれているのを、<br>
　よく見かけますが、細かく関数を作って、処理を見やすくしましょう。<br>
　やり方は後述します。<br>
</div>

### クラス
Unity（C#）ではこのクラスを使ってプログラミングを行います。<br>
ゲーム内に登場するオブジェクト事にクラスを用意して、そのオブジェクトが何をするか、<br>
を基準に考えながらプログラムを行います。<br>
このような、登場する物や仕組みを軸にプログラミングを行う事をオブジェクト指向と言います。<br>
```clike
	public class Player:MonoBehaviour// ←これがクラス
	{
		int hp; 

		void Start()
		{
			Debug.Log("HP:" + hp);
		}
	}
```

## Unityプロジェクト
### 初期設定
プロジェクトをUnity6、3DURP、で作成してください。（あるなら6000.50ver)<br>
その後下記のパスに上がっている物をDL・解答して、<br>
Asset直下にいれてください。<br><br>
+ Assets＞Member＞Sceneのシーンをすべて登録<br>
+ TextMeshProUGUIをインポート<br>
+ Titleシーンを開く<br>
### 操作方法
マウス移動　視点移動<br>
WASD　キャラクター移動<br>
SPACE　ジャンプ<br>
SHIFT　ダッシュ移動<br>
ENTER　タイトル：ゲームスタート　インゲーム：リスタートorネクストステージ<br>
### スクリプト解説
#### 変数の使用例
#### 関数の使用例
#### 条件分岐の使用例
#### クラスの使用例
### ギミック関係の作り方
### マップ関係の作り方
### プログラムなんて書かないほうが良い

