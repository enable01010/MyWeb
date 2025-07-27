# 出力
## 文字列の出力
文字の表示はprintf()を使って表示する事が出来ます。
```
string text = "paiza";
printf(paiza.c_str());
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  paiza
</div>

## 数値の出力
数値の表示はフォーマット指定子を使う事で表示する事が出来ます。
```
int number = 0;
printf("%d",number);
```
<div style="border-left: 5px solid #2d9cdb; background: #e8f4fd; padding: 0.8em; margin: 1em 0;">
  <strong>💡 出力結果：</strong><br>
  0
</div>

## 改行の出力
改行の表示はエスケープシーケンスを使う事で表示する事が出来ます。
```
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
```
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

# 入力
## 1行受け取り
## スペース区切りで受け取り
# 文字列操作
## 文字列の長さ
## 文字列が含まれているか
## 置き換え
## 部分削除
## 追加・挿入
## 反転
# 配列操作
## 配列の受け取り
## 配列のソート
## 配列の合計
## 2次元配列