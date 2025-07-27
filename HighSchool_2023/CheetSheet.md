# パイザ C++ チートシート
<br>
<br>
<br>
<br>

# 出力

## 文字列の出力
文字の表示はprintf()を使って表示する事が出来ます。
```clike
string text = "paiza";
printf(paiza.c_str());
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  paiza
</div>

## 数値の出力
数値の表示はフォーマット指定子を使う事で表示する事が出来ます。
```clike
int number = 0;
printf("%d",number);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  0
</div>

## 改行の出力
改行の表示はエスケープシーケンスを使う事で表示する事が出来ます。
```clike
int number1 = 0;
int number2 = 1;
printf("%d",number1);
printf("\n");
printf("%d",number2);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  0 <br>
  1
</div>

## 複雑な出力
フォーマット指定子やエスケープシーケンスを組み合わせる事で複雑な文章を表示する事が出来ます。
```clike
string text = "text";
int number = 123;
printf("%s\n%d\nあいうえお",text,number);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  text<br>
  123<br>
  あいうえお
</div>

<br>
<br>
<br>
<br>

# 入力

## 1行受け取り
1行の受け取りはgetline()を使う事で実装出来ます。
```clike
string text;
getline(cin,text);
```
<div style="border-left: 5px solid #f39c12; background: #fff7e6; padding: 0.8em; margin: 1em 0;">
  <strong>📌 重要：</strong><br>
  getlineはstring型でしか受け取ることが出来ません。
  数値を受け取りたい場合は下記の内容が必要です。
</div>
```clike
string text;
getline(cin,text);
int number = stoi(text);
```

## スペース区切りで受け取り
スペース区切りの受け取りはcinを使う事で実装出来ます。
```clike
string text;
cin >> text;
```
```clike
int number;
cin >> number;
```

<div style="border-left: 5px solid #c0392b; background: #fdecea; padding: 0.8em; margin: 1em 0;">
  <strong>🚨 注意：</strong><br>
  getlineとcinを一緒に使う事はできません。
  一つの問題に付きどちらか片方しか使えないので注意してください。
</div>


<br>
<br>
<br>
<br>

# 文字列操作

## 文字列の長さ
文字の長さは.length()で取得する事が出来ます。
```clike
string text = "test";
int number = text.length();
printf("%d",number);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  4
</div>

## 文字列が含まれているか
特定の文章に、指定の文字が含まれているかは.findで調べられます。<br>
見つからない時 →　-1<br>
見つかった時　→　何文字目から指定の文字含まれるか
```clike
string text = "paizaLesson";
string target = "Lesson";
int number = text.find(target);
printf("%d",number);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  5
</div>


## 置き換え
特定の文章の一部を置き換える場合は.replaceを使う事で置き換える事が出来ます。
```clike
string text = "paizaLesson";
int startNumber = 5;
int length = 6;
string afterText = "Training";
text.replace(startNumber,length,afterText);
printf(text.c_str()_);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  paizaTraining
</div>

## 部分削除
特定の文章の一部を消す場合は.eraseを使うことで実装出来ます。
```clike
string text = "paizaTraining";
int startNumber = 5;
int length = 8;
text.erase(startNumber,length);
printf(text.c_str()_);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  paiza
</div>


## 追加・挿入
追加・挿入は.insertを使う事で実装出来ます。
```clike
string text = "paiza";
int pos = 5;
string insertText = "Lesson";
text.insert(pos,insertText);
printf(text.c_str()_);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  paizaLesson
</div>

<br>
<br>
<br>
<br>

# 配列操作

## 配列の受け取り
パイザで配列を受け取る時は下記のように実施する事で受け取る事が出来ます。
```clike
int count;
cin >> count;
int numbers[count];
for(int i = 0; i < count;i++)
{
	cin >> numbers[i];
}
```

## 2次元配列
パイザで２次元配列を受け取る時は下記のように実施する事で受け取る事が出来ます。
```clike
int xLength;
int yLength;
cin >> xLength;
cin >> yLength;
int numbers[yLength][xLength];
for(int y = 0; y < yLength;y++)
{
	for(int x = 0; x < xLength;x++)
	{
		cin >> numbers[y][x];
	}
}
```