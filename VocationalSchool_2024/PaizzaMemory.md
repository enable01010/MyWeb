# メモリと集合

# 授業目的
この授業では、プログラムの根幹をなしているメモリについて学びます。<br>
現在のゲームが稼働する環境でメモリを極限まで制限する場面は正直、稀です。<br>
個人でゲームを作る場合、この知識がネックになる事はほとんどありません。<br>
ただ、オンライン通信でのデータのやり取りや、コマンドパターン（デザインパターンの一つ）等、いくつかの場面でメモリの知識は必須になります<br>
※IT・ゲーム問わず、就活の問題でもよく見る<br>

メモリの知識をもってコーディングができるとプログラムの高速化やメモリ使用量の削減が可能になります。<br>
メモリについて意識してプログラムを書けるかどうかは別として、知識として知らないのは問題なので、
この機会にメモリについて学びましょう。<br>

# メモリとは
## 2進数
皆さんが普段使っている数字は10進数です<br>
10進数は0～9までの10種類の数字を使って数を表現します<br>

一方、コンピュータは2進数を使って数を表現します<br>
2進数は0と1の2種類の数字を使って数を表現します<br>

### シフト演算
シフト演算はビットを左右にずらす演算です<br>
~~~csharp
int num = 1; // 0000 0001
num = num << 1; // 左に1ビットシフト 0000 0010 (2進数) → 2 (10進数)
num = num << 2; // 左に2ビットシフト 0000 1000 (2進数) → 8 (10進数)
num = num >> 1; // 右に1ビットシフト 0000 0100 (2進数) → 4 (10進数)
~~~

### 論理和
論理和はビットごとにOR演算を行います<br>
~~~csharp
int a = 0b_1100; // 12 (10進数)
int b = 0b_1010; // 10 (10進数)
int result = a | b; // 論理和 0b_1110 (2進数) → 14 (10進数)
~~~

### 論理積

論理積はビットごとにAND演算を行います<br>
~~~csharp
int a = 0b_1100; // 12 (10進数)
int b = 0b_1010; // 10 (10進数)
result = a & b; // 論理積 0b_1000 (2進数) → 8 (10進数)
~~~


### 排他的論理和
排他的論理和はビットごとにXOR演算を行います<br>
~~~csharp
int a = 0b_1100; // 12 (10進数)
int b = 0b_1010; // 10 (10進数)
int result = a ^ b; // 排他的論理和 0b_0110 (2進数) → 6 (10進数)
~~~
いったんパイザ<br>

## ビットとバイト
### 基本的な変数のメモリ使用量
メモリーとは先ほどの２進数の0と1を保存する場所です<br>
1ビット(bit)は0か1のどちらか1つの情報を保存します<br>
8ビット(bit)で1バイト(byte)となります<br>
一般的な変数のメモリ使用量は以下の通りです(C#)<br>
<br>
| データ型 | メモリ使用量 |<br>
| --- | --- |<br>
| bool | 1バイト |<br>
| byte | 1バイト |<br>
| char | 2バイト |<br>
| short | 2バイト |<br>
| int | 4バイト |<br>
| long | 8バイト |<br>
| float | 4バイト |<br>
| double | 8バイト |<br>


## よく使うメモリの省エネ(Enum)
### Enumの事前知識
まずEnumはバイト数を指定できる<br>
~~~csharp
enum EnemyType : byte
{
    sample1,
    sample2,
}
~~~
Enumはビット演算で組み合わせが可能<br>
~~~csharp
enum EnemyType : byte
{
    Sample1 = 1 << 0, // 1
    Sample2 = 1 << 1, // 2
    Sample3 = 1 << 2, // 4
    Sample4 = 1 << 3, // 8
}

enum EnemyType2 : byte
{
    Sample1 = 0b1,      // 1
    Sample2 = 0b10,     // 2
    Sample3 = 0b100,    // 4 
    Sample4 = 0b1000,   // 8
}
~~~
### Enumをboolの集合体としてつかう
Enumをビット演算で組み合わせることで、boolの集合体として使うことが出来る<br>
~~~csharp
enum StateType : short
{
    Sleep =     0b00000001,     // 睡眠
    Burn =      0b00000010,      // 火傷
    Paralysis = 0b00000100, // 麻痺
    Chaos =     0b00001000,     // 混乱
    Poison =    0b00010000,    // 毒 
    Frozen =    0b00100000,    // 氷
    Death =     0b01000000,     // ひん死
}
~~~
boolを7個使うと7バイト必要だが、Enumを使うと2バイトで済む<br>
        
### 論理積で出来る状態確認

~~~csharp
[Flags]
enum StateType : short
{
    Sleep =     0b00000001,     // 睡眠
    Burn =      0b00000010,     // 火傷
    Paralysis = 0b00000100,     // 麻痺
    Chaos =     0b00001000,     // 混乱
    Poison =    0b00010000,     // 毒 
    Frozen =    0b00100000,     // 氷
    Death =     0b01000000,     // ひん死


    // 判定用
    DontMove = Sleep | Paralysis | Frozen | Chaos, // 動けない状態
    Damage = Burn | Poison, // 継続ダメージ状態
}

void main()
{
    StateType status = CheeckType();//割愛、状態を選別
    
    if((status & EnemyType.DontMove) != 0)
    {
        // 動けない
    }
    if((status & EnemyType.Damage) != 0)
    {
        // 継続ダメージ
    }

    //　NGパターン
    if(status == EnemyType.Sleep || status == EnemyType.Paralysis || status == EnemyType.Frozen || status == EnemyType.Chaos)
    {
        // 動けない
    }
}

~~~

### 排他的論理和の使い道
複数の状態が同時に発生しない場合、XORを使うことで条件分岐を簡潔にできる<br>
~~~csharp
void main()
{
    if(Input.GetKey(KeyCode.LeftArrow) ^ Input.GetKey(KeyCode.RightArrow))
    {
        // 左右どちらか一方が押されている
    }
}
~~~

値の入れ替えにも使える<br>
一応、一般的なやり方より仮置きの変数がないためメモリ使用量が少ない<br>
~~~csharp
void main()
{
    int a = 5;
    int b = 10;
    // 値の入れ替え
    a = a ^ b;
    b = a ^ b;
    a = a ^ b;
}
~~~


### int型を複数の数値として使う
int型をビット演算で分割して複数の数値として使うことが出来る<br>
特に、0～255までの数値を複数保存したい場合に有効<br>
UnityのColorを同じようにしてみると、、、<br>
~~~csharp
void main()
{
    int color = 0;
    byte r = 255;
    byte g = 128;
    byte b = 64;
    byte a = 255;
    // 色を保存
    color |= r << 24; // R
    color |= g << 16; // G
    color |= b << 8;  // B
    color |= a << 0;  // A
    // 色を取得
    byte getR = (byte)((color >> 24) & 0b1111);
    byte getG = (byte)((color >> 16) & 0b1111);
    byte getB = (byte)((color >> 8) & 0b1111);
    byte getA = (byte)((color >> 0) & 0b1111);
}
~~~

### この辺からは趣味レベル
計算速度の差 <br>
論理和論理積、足し算引き算は１サイクル（プログラムに置ける最小単位）<br>
掛け算は数サイクル<br>
除算は数十サイクル<br>

上を元に考えると,,,<br>
a * 2 より　a + a の方が速い<br>
a / 10 より　a * 0.1 の方が速い<br>

if(num > 5) と　if(num > 0) と　if(num != 0) の速度差<br>
左から順に遅い<br>

これを踏まえた上でfor文の処理は、、、<br>
~~~ csharp
void main()
{
    for(int i = 0; i < 100; i++) // 普通のやり方
    {
        // 処理
    }

    for(int i = 100; i != 0; i--) // 少し速いやり方
    {
        // 処理
    }
}
~~~

※昔のデバイスでは有効だったが、現在のCPUではあまり意味が無い<br>
誤差１％以下の超極端な話なので、プログラムの可読性を優先しましょう<br>

ただし、例外として、シェーダープログラムでは意味がある場合があります<br>
1920*1080のフルHD解像度でピクセルシェーダーを動かす場合、約200万回の処理が走ります<br>
その場合、誤差１％でも20,000回分の処理時間が変わるので、意味が出てきます<br>
又、掛け算割り算のサイクル数の差も無視できなくなります<br>