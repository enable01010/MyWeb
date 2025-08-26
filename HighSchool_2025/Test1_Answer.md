# テスト 7/29　の回答

## Question1
3*5の計算をプログラムで行い出力してください。<br>

~~~ clike
void Question1()
{
    // 3*5の計算をプログラムで行い出力してください。
    int number = 3 * 5;
    printf("%d", number);
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  数値（int）の変数　number に　3*5の計算結果を保存して、<br>
  printf()にてnumberの値を表示しています。
</div>

## Question2
九九の表をスペース区切りで出力してください。<br>
~~~ clike
void Question2()
{
    // 九九の表をスペース区切りで出力してください。
    for (int i = 1; i < 10; i++)
    {
        for (int j = 1; j < 10;j++)
        {
            int number = i * j;
            if (number < 10)
            {
                printf("%d  ",number);
            }
            else
            {
                printf("%d ", number);
            }
        }
        printf("\n");
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  九九の表などを作成する場合にはfor文を2重にすることで実装することができます。
  iの段のj個目の掛け算をすることで表のように表現することができます。
</div>


## Question3
1000000以下の素数を計算によって求めすべて出力してください。<br>
~~~ clike
void Question3()
{
    // 1000000以下の素数を計算によって求めすべて出力してください。
    int count = 100;
    for (int i = 2; i < count;i++)
    {
        bool isSosu = true;
        for (int j = 2; j < i;j++)
        {
            if (i % j == 0)
            {
                isSosu = false;
                break;
            }
        }

        if (isSosu == true)
        {
            printf("%d\n",i);
        }
    }
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  素数の定義は１とその数以外で割り切れない数字です。
  なので、プログラムでその数まですべて割り切る作業をしてあげると素数を求めることができます。
</div>


<div style="border-left: 5px solid #f39c12; background: #fff7e6; padding: 0.8em; margin: 1em 0;">
  <strong>📌 重要：</strong><br>
  Question2の表のようなfor文の使い方とQuestion3のようなi番目までの要素すべてを再確認するような使い方は、
  for文の活用例としてよく見かけます。なんとなくでいいので、数値の動きをイメージできるようにしましょう。
</div>


## Question4
1回入力の受け取りを行い、<br>
その受け取り結果に、"test"と含まれていたら"Yes"、含まれていなかったら"No"と出力してください。<br>
~~~ clike
void Question4()
{
    // 1回入力の受け取りを行い、
    // その受け取り結果に、"test"と含まれていたら"Yes"、含まれていなかったら"No"と出力してください。
    string yesText = "Yes";
    string noText = "No";
    string target = "test";

    string input;
    getline(cin, input);
    
    if (input.find(target) == -1)
    {
        printf(noText.c_str());
    }
    else
    {
        printf(yesText.c_str());
    }
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
  C++の言語では、findを使うことで、文字列に含まれているかどうかを判定することができます。
  input.find(target)の回答が-1であれば含まれていない。
  それ以外であればどこかしらに含まれている状態になります。
  このfindはパイザで稀に使うので覚えておくと便利でしょう。
</div>

## Question5
2回数値の入力受け取りを行い、<br>
その二つの数字の四則演算の結果をスペース区切りで出力してください。。（順番は+-*/）<br>
~~~ clike
void Question5()
{
    // 2回数値の入力受け取りを行い、
    // その二つの数字の四則演算の結果をスペース区切りで出力してください。。（順番は+-*/）

    int number1, number2;
    cin >> number1 >> number2;

    printf("%d\n", number1 + number2);
    printf("%d\n", number1 - number2);
    printf("%d\n", number1 * number2);
    printf("%d\n", number1 / number2);
}
~~~

## Question6
1回数値の入力受け取りを行い、<br>
その数が偶数の場合”偶数”、奇数の場合"奇数"と出力してください。<br>
~~~ clike
void Question6()
{
    // 1回数値の入力受け取りを行い、
    // その数が偶数の場合”偶数”、奇数の場合"奇数"と出力してください。
    string gusu = "偶数";
    string kisu = "奇数";
    int number;
    cin >> number;

    if (number % 2 == 0)
    {
        printf(gusu.c_str());
    }
    else
    {
        printf(kisu.c_str());
    }
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
    偶数奇数の判断は2で割ったときのあまりがあるかないかで判断することができます。
    （〇〇で割り切れる数も同様にできます。）
    ゲームでも偶数プレイヤーのみ〇〇等の処理が多々あるので覚えておきましょう。
</div>

## Question7
10回数値の入力受け取りを行い、<br>
その中で最も大きい数を出力してください。<br>
~~~ clike
void Question7()
{
    // 10回数値の入力受け取りを行い、
    // その中で最も大きい数を出力してください。
    int numbers[10];
    for (int i = 0; i < 10;i++)
    {
        cin >> numbers[i];
    }

    int max = -999999999;
    for (int i = 0; i < 10;i++)
    {
        if (max < numbers[i])
        {
            max = numbers[i];
        }
    }

    printf("%d",max);
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
    for文を活用することで特定の要素の中の一番大きい数字や小さい数字を選出することができます。
    下の問題のソートと組み合わせて使うことが多いです。
    覚えておきましょう。
</div>

## Question8
10回数値の入力受け取りを行い、<br>
それらを小さい順にして、スペース区切りで表示してください。<br>
~~~ clike
void Question8()
{
    // 10回数値の入力受け取りを行い、
    // それらを小さい順にして、スペース区切りで表示してください。

    int numbers[10];
    for (int i = 0; i < 10;i++)
    {
        cin >> numbers[i];
    }

    for (int i = 0; i < 10;i++)
    {
        int min = 999999999;
        int count = i;
        for (int j = i; j < 10;j++)
        {
            if (min > j)
            {
                min = j;
                count = j;
            }
        }

        int temp = numbers[i];
        numbers[i] = numbers[count];
        numbers[count] = temp;
    }

    for (int i = 0; i < 10;i++)
    {
        printf("%d", numbers[i]);
    }
}
~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
    ソートはゲーム製作でもよく見かけます。
    ランキング表示など、比較的によく使うので調べて実装できるようにしておきましょう。
</div>

## Question9
１回の入力受け取りを行い、<br>
その入力の内容が正しい場合に"Yes"、間違っている場合は"No"と表示してください。<br>
入力は下記のような四則演算の式です。<br>
4 * 5 = 20<br>
式は必ず、〇 * 〇＝〇のような二つの数字の計算結果を求めるものです。<br>
~~~ clike
void Question9()
{
    // １回の入力受け取りを行い、
    // その入力の内容が正しい場合に"Yes"、間違っている場合は"No"と表示してください。
    // 入力は下記のような四則演算の式です。
    // 4 * 5 = 20
    // 式は必ず、〇 * 〇＝〇のような二つの数字の計算結果を求めるものです。

    string yesText = "Yes";
    string noText = "No";

    int firstNumber;
    char kigou;
    int secondNumber;
    char equal;
    int answerNumber;
    
    cin >> firstNumber >> kigou >> secondNumber >> equal >> answerNumber;
    string answerText = noText;
    switch (kigou)
    {
    case '+':
        if (firstNumber + secondNumber == answerNumber) answerText = yesText;
        break;
    case '-':
        if (firstNumber - secondNumber == answerNumber) answerText = yesText;
        break;
    case '/':
        if (firstNumber / secondNumber == answerNumber) answerText = yesText;
        break;
    case '*':
        if (firstNumber * secondNumber == answerNumber) answerText = yesText;
        break;
    }
    printf(answerText.c_str());
}
~~~
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
    この辺からは発展問題になります。
    この問題で大切なのは、データを分割して受け取ることです。
    データを分割して受け取れたら、それを区別して並べてあげることで判定をすることができます。
</div>

## Question10
10回の入力受け取りを行い、キャラクターの座標をx, yを主出力してください。<br>
入力はWASDのいずれか１文字です。<br>
・Wキーの場合Y座標を１プラス<br>
・Aキーの場合はＸ座標を１マイナス<br>
・Ｓキーの場合はＹ座標を１マイナス<br>
・Ｄキーの場合はＸ座標を１プラス<br>
キャラクターの初期座標はx = 0, y = 0です。<br>
~~~ clike
void Question10()
{
    // 10回の入力受け取りを行い、キャラクターの座標をx, yを主出力してください。
    // 入力はWASDのいずれか１文字です。
    // ・Wキーの場合Y座標を１プラス
    // ・Aキーの場合はＸ座標を１マイナス
    // ・Ｓキーの場合はＹ座標を１マイナス
    // ・Ｄキーの場合はＸ座標を１プラス
    // キャラクターの初期座標はx = 0, y = 0です。

    int x = 0, y = 0;
    char text;
    for (int i = 0; i < 10;i++)
    {
        cin >> text;
        switch (text)
        {
        case 'w':
            y++;
            break;
        case 'a':
            x--;
            break;
        case 's':
            y--;
            break;
        case 'd':
            x++;
            break;
        }
    }

    printf("%d %d", x, y);
    
}

~~~

<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 解説</strong><br>
    for文の中でも入力を受け取ったりすることはできます。
    指定の回数入力を受け取ってあげることで、
    Ｘ、Ｙのデータを適切に管理することができます。
</div>



## 全体
~~~ clike

#include <iostream>
#include <string>
using namespace std;

void Question1()
{
    // 3*5の計算をプログラムで行い出力してください。
    int number = 3 * 5;
    printf("%d", number);
}

void Question2()
{
    // 九九の表をスペース区切りで出力してください。
    for (int i = 1; i < 10; i++)
    {
        for (int j = 1; j < 10;j++)
        {
            int number = i * j;
            if (number < 10)
            {
                printf("%d  ",number);
            }
            else
            {
                printf("%d ", number);
            }
        }
        printf("\n");
    }
}

void Question3()
{
    // 1000000以下の素数を計算によって求めすべて出力してください。
    int count = 100;
    for (int i = 2; i < count;i++)
    {
        bool isSosu = true;
        for (int j = 2; j < i;j++)
        {
            if (i % j == 0)
            {
                isSosu = false;
                break;
            }
        }

        if (isSosu == true)
        {
            printf("%d\n",i);
        }
    }
}

void Question4()
{
    // 1回入力の受け取りを行い、
    // その受け取り結果に、"test"と含まれていたら"Yes"、含まれていなかったら"No"と出力してください。
    string yesText = "Yes";
    string noText = "No";
    string target = "test";

    string input;
    getline(cin, input);
    
    if (input.find(target) == -1)
    {
        printf(noText.c_str());
    }
    else
    {
        printf(yesText.c_str());
    }
}

void Question5()
{
    // 2回数値の入力受け取りを行い、
    // その二つの数字の四則演算の結果をスペース区切りで出力してください。。（順番は+-*/）

    int number1, number2;
    cin >> number1 >> number2;

    printf("%d\n", number1 + number2);
    printf("%d\n", number1 - number2);
    printf("%d\n", number1 * number2);
    printf("%d\n", number1 / number2);
}

void Question6()
{
    // 1回数値の入力受け取りを行い、
    // その数が偶数の場合”偶数”、奇数の場合"奇数"と出力してください。
    string gusu = "偶数";
    string kisu = "奇数";
    int number;
    cin >> number;

    if (number % 2 == 0)
    {
        printf(gusu.c_str());
    }
    else
    {
        printf(kisu.c_str());
    }
}

void Question7()
{
    // 10回数値の入力受け取りを行い、
    // その中で最も大きい数を出力してください。
    int numbers[10];
    for (int i = 0; i < 10;i++)
    {
        cin >> numbers[i];
    }

    int max = -999999999;
    for (int i = 0; i < 10;i++)
    {
        if (max < numbers[i])
        {
            max = numbers[i];
        }
    }

    printf("%d",max);
}

void Question8()
{
    // 10回数値の入力受け取りを行い、
    // それらを小さい順にして、スペース区切りで表示してください。

    int numbers[10];
    for (int i = 0; i < 10;i++)
    {
        cin >> numbers[i];
    }

    for (int i = 0; i < 10;i++)
    {
        int min = 999999999;
        int count = i;
        for (int j = i; j < 10;j++)
        {
            if (min > j)
            {
                min = j;
                count = j;
            }
        }

        int temp = numbers[i];
        numbers[i] = numbers[count];
        numbers[count] = temp;
    }

    for (int i = 0; i < 10;i++)
    {
        printf("%d", numbers[i]);
    }
}

void Question9()
{
    // １回の入力受け取りを行い、
    // その入力の内容が正しい場合に"Yes"、間違っている場合は"No"と表示してください。
    // 入力は下記のような四則演算の式です。
    // 4 * 5 = 20
    // 式は必ず、〇 * 〇＝〇のような二つの数字の計算結果を求めるものです。

    string yesText = "Yes";
    string noText = "No";

    int firstNumber;
    char kigou;
    int secondNumber;
    char equal;
    int answerNumber;
    
    cin >> firstNumber >> kigou >> secondNumber >> equal >> answerNumber;
    string answerText = noText;
    switch (kigou)
    {
    case '+':
        if (firstNumber + secondNumber == answerNumber) answerText = yesText;
        break;
    case '-':
        if (firstNumber - secondNumber == answerNumber) answerText = yesText;
        break;
    case '/':
        if (firstNumber / secondNumber == answerNumber) answerText = yesText;
        break;
    case '*':
        if (firstNumber * secondNumber == answerNumber) answerText = yesText;
        break;
    }
    printf(answerText.c_str());
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

    int x = 0, y = 0;
    char text;
    for (int i = 0; i < 10;i++)
    {
        cin >> text;
        switch (text)
        {
        case 'w':
            y++;
            break;
        case 'a':
            x--;
            break;
        case 's':
            y--;
            break;
        case 'd':
            x++;
            break;
        }
    }

    printf("%d %d", x, y);
    
}

int main()
{
    // Question1();
    // Question2();
    // Question3();
    // Question4();
    // Question5();
    // Question6();
    // Question7();
    // Question8();
    // Question9();
    Question10();

}

~~~
