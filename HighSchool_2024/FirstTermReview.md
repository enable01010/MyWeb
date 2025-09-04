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
## パイザ
### 標準入力・標準出力
### 便利な関数<Linq>
## Unity
### よく使う処理
## 就活に向けて
### 就活の開始時期
### ポートフォリオ