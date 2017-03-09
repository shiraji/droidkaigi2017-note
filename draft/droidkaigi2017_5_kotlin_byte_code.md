# Kotlin byte code

* デコンパイルボタンで一発やで。

## null許容型

関数の引数が非null型なら事前条件を追加する。
他にもnullチェックをしっかり追加している。

## 関数型/ラムダ式

(View) -> UnitはJavaではFunction1

関数型 : FunctionN interfaceを実装する
ラムダ式 ; 無名クラスを実装する

## 拡張関数

拡張する側を第一引数にして、static関数にする

## Property

getter/setterを生成。val/varによっての違いもあり。
Lombokに動作的にも近い。

data classも同じような結果となる。

## 設計に与える影響

### null許容型

findViewByIdを使うとnull許容型になってしまう以上、それを避けるために、Databinding使ったりを検討すべき。

### 拡張関数

コード上の意図が明確になる

Q Kotlinの寿命

A Jetbrains製だし、Javaだから戻せる。



Q Kotlin間での互換性

A 1.0以降であればあり。


