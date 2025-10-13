# パイザ配列

## 授業目的

パイザのC・B問題で頻出する配列系のデータを用いて解答する問題に、<br>
スムーズに答えられるようになりましょう。<br>
<br>
パイザでの就活はBとCで大きな差があります。<br>
一つの目標として、Bが取れることを目指しましょう。<br>

## 配列の受取り方
パイザでは、よくこのような入力の形式で問題が出されます。

/////////////////////////////////////////////////////////////////////<br>
入力の1行目で次の行にいくつデータがあるかがあります。<br>
2行目にはスペース区切りでデータその個数の数値が与えられるので、<br>
それを小さい順に並べて出力してください。<br>
<br>
入力例<br>
5<br>
10 7 3 1 4<br>
<br>
出力<br>
1 <br>
3 <br>
4 <br>
7 <br>
10<br>
/////////////////////////////////////////////////////////////////////<br>


~~~ clike
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
	static void Main()
	{
		// 1行目の受取り
		string input = Console.ReadLine();
		
		// 2行目の受取り
		string input2 = Console.ReadLine();
		List<string> datasStr = input2.Split(' ').ToList();
		
		// 配列の内容をString→intに変更
		List<int> data = datasStr .Select(int.Parse).ToList();

		// ソート
		datas = datas.OrderBy(n => n).ToList();

		// 出力
		for(int i = 0; i < data.Count;i++)
		{
			Console.WriteLine(data[i].ToString());
		}
	}
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  C#で行う場合は、1行目で受け取るデータの個数が必要ない場合もあります。<br>
  又、今回はわかりやすくするために、Listの操作を分割しましたが、Linqは配列操作を以下つで行う<br>
  もののため下のように書くのが一般てきです。<br>
</div>

~~~ clike
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
	static void Main()
	{
		// 1行目の受取り
		string input = Console.ReadLine();
		
		// 2行目の受取り
		string input2 = Console.ReadLine();

		// データの変換
		List<int> datas = 
			input2
				.Split(' ')			//スペース区切りに変更
				.Select(int.Parse)	//String→intに変換
				.OrderBy(n => n)	//小さい順にソート
				.ToList();			//リストに確定

		// 出力
		for(int i = 0; i < data.Count;i++)
		{
			Console.WriteLine(data[i].ToString());
		}
	}
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 ちなみに</strong><br>
  このListないしLinqはゲーム制作においてはソート機能とかに使われることが多いです。<br>
  スマホゲームでキャラクターBox系で自由に項目選んでソートしたりする際にこのListを使います。<br>

  他にも、シュミレーションゲーム等で攻撃範囲内のユニットを一覧化したり、用途は多岐にわたるので、<br>
  使えるようになって置くと便利です。<br>
</div>

## 2次元配列
同じくパイザでは２次元配列を用いて問題に解答することがあります。<br>
２次元配列では、Listのような処理をする必要はないので、一般的な２次元配列を使うことをおすすめします。<br>

