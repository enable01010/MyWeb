# テスト 7/29　

## 問題の取り込みかた
VisualStuidoを開いて、コンソールアプリ　(C++,windows,コンソール）のプロジェクトで、<br>
プロジェクト名を自分の名前にして作成してください.。


新しいプロジェクトの作成<br>
<img src="Image/VS_HowCreate_1.png" height="300">
プロジェクトの種類選択<br>
<img src="Image/VS_HowCreate_2.png" height="150">
プロジェクトの名前（自分の名前をいれてください）<br>
<img src="Image/VS_HowCreate_3.png" height="600">

自動生成されたプログラムをすべて削除して、下記のプログラムを貼り付けてください。
~~~ clike
#include <iostream>
#include <string>
using namespace std;

void Question1()
{
    // 3*5の計算をプログラムで行い出力してください。
}

void Question2()
{
    // 九九の表をスペース区切りで出力してください。
}

void Question3()
{
    // 1000000以下の素数を計算によって求めすべて出力してください。
}

void Question4()
{
    // 1回入力の受け取りを行い、
    // その受け取り結果に、"test"と含まれていたら"Yes"、含まれていなかったら"No"と出力してください。
}

void Question5()
{
    // 2回数値の入力受け取りを行い、
    // その二つの数字の四則演算の結果をスペース区切りで出力してください。。（順番は+-*/）
}

void Question6()
{
    // 1回数値の入力受け取りを行い、
    // その数が偶数の場合”偶数”、奇数の場合"奇数"と出力してください。
}

void Question7()
{
    // 10回数値の入力受け取りを行い、
    // その中で最も大きい数を出力してください。
}

void Question8()
{
    // 10回数値の入力受け取りを行い、
    // それらを小さい順にして、スペース区切りで表示してください。
}

void Question9()
{
    // １回の入力受け取りを行い、
    // その入力の内容が正しい場合に"Yes"、間違っている場合は"No"と表示してください。
    // 入力は下記のような四則演算の式です。
    // 4 * 5 = 20
    // 式は必ず、〇 * 〇＝〇のような二つの数字の計算結果を求めるものです。
}

void Question10()
{
    // 10回の入力受け取りを行い、キャラクターの座標をx, yを主出力してください。
    // 入力はWASDのいずれか１文字です。
    // ・Wキーの場合Y座標を１プラス
    // ・Aキーの場合はＸ座標を１マイナス
    // ・Ｓキーの場合はＹ座標を１マイナス
    // ・Ｄキーの場合はＸ座標を１プラス
    // キャラクターの初期座標はx = 0, y = 0です。
}

int main()
{
    Question1();
    // Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    // Question10();

}

~~~

## 問題の解き方
問題用の関数が用意されています<br>
その関数の中身を実装してください。<br>
例：問題1を解く場合（答えは間違っています。）<br>

~~~ clike
#include <iostream>
#include <string>
using namespace std;

void Question1()
{
    // 3*5の計算をプログラムで行い出力してください。
    int number = 5;
    int number = 3;
    int answer = number * number;
    printf("%d",number);
}
~~~

## 問題の切り替え方
プログラムの一番下にint main()があります。<br>
int main()の中にある関数のコメントアウトを入れ替える事で表示する問題をきりかえる事ができます。<br>
例：問題2を解く場合
~~~ clike
#include <iostream>
#include <string>
using namespace std;

int main()
{
    // Question1();
    Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    // Question10();

}
~~~