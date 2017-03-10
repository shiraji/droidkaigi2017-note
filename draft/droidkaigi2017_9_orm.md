# ORMの選び方

Android-ormaはまだ完璧じゃないけど、どうしても欲しい機能は追加している。

どういうところにORMを作るときに着目すると良いか。

SQLiteHelperでゴリゴリやるより、どう考えてもORMapperを使ったほうが良い。

## なんでデータ保存する？

行動ログなどをBufferやQueueで保存して、あとで送信するなどの仕組みがあるといいよ

## ORMs

GitHubではすでにスター100超えているライブラリは何個もある。みんな理想的なものがないから作りたくなってしまうのでは？

使うものを悩むのが問題？

## ORMapping

テーブル<->プログラム間をserialize/deserializeする

## Query Builder

採用しているORMによって結構書き方が違う

* todo.quals("title", title) // AA / タイポに弱い。型エラーにならない。最悪実行時エラーにもならない。
* todo.equals(Todo_Meta.title, title) // requery/greendao / コンパイル時に生成。タイポでコンパイルエラーになってくれる。しかも型安全になっている。
* todo.titleEq(title) // Orma / コンパイルエラー、型安全。入力しやすいし、短い。

ORMapperは機能がありすぎるので、ドキュメント読まないものが良い。

## Association(or relationship)

relationと似ているから、あえてAssociationと呼んでいる。(ActiveRecordとかも)

* has-one/has-many/many-to-many

ORMapperによって結構違っている。実装が面倒なのでサポートしなかったり、頑張っていたり。

## pub-sub

データの変更を通知してくれる。
複数のFragmentでスターとかの同期をする場合便利。

ORMapperとしてはそこまで必須ではないが、最近はだいだいサポートされている。

## Migration

SQLで考えると、どのタイミングでAlter tableするか？の判断。

実際にやると結構たいへん。にしては開発時に結構利用する。

## OSSとしてどうか？

ドキュメント、CI/CD(というかリリース頻度)、コミッター数、CHANGELOG、最近の活動。

これらは見ればわかるから省略

## 比較

## AA

簡単に使える。
ORMAでも参考にした。
Reflectionが多く、コードが煩雑でネタとなってる。
暗黙的にPrimaryKeyを作成している。が、クッ社でもID付与しちゃったりしていて、やっぱり明示的にやるべきだよね。

Railsのsaveメソッドと同じような感じで便利。

SQLをかなり強く意識する必要が出て来る。

outerJoinも簡単に出来る。(->ORMAでも言われるけど未実装)

Associationもこれ以上ないくらいシンプル。

pub/subもしっかり出来ている。

5年前に作ったものにしては本当に洗練されている。

マイグレーションは酷い。
　: 開発時はアンインストールしたほうが早い。
クラッシュタイミングもRuntime時なのでツラい

## greenDAO

速度が早く、結構それを求めて使われているっぽい。

メソッドがたくさん勝手に生える。書いたコードに生える。
ロジックを書くとカオスになるので、最終的には書くなというフローになるはず。

人類には難しい

Associationの挿入タイミングなどは自分で書く。

Migration/pub-subは未対応。

## requwry

2016/9にv1.0.0

abstract classかinterfaceを定義する2種類の方法で実装する

RxJava1/2の両方とも対応もされている。

selectなどの戻り値がResultクラスでStream生やしたりできるので、かなりモダン。

Associationは自分で挿入タイミングを示さないと駄目。

Migrationはscheme versionを上げればいける。が、開発時に上げるか不明。

## Realm

extendsする必要あり、getter/setterも必要。

insert時にtransaction必要なので、ネスト深くなる。

Association/pub-subはサポート

Realm Mobile Platformは裏側でやれるので便利。

Migrationは結構大変。他のやつに比べてもツラい。


## Orma

baseクラスが必要なく、フィールドをfinalとかにも出来る。

あえて、遅い操作が出来ないようにしている。Indexがはっていないカラムに対してSelectメソッドを提供していない。

upsertメソッドは便利やで。

pub-subはまだexperimental

migrationはschema-diff。手で書くことも出来るよ。
仕組みは簡単でSchemaDiffMigrationでやっていて、gitと同じような感じ。
SCHEME_HASHでVersioningをしている。

GitHubでは英語だけどTwitterでは日本語でOK。








