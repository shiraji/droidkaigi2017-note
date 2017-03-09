# オフラインファーストのアプリ開発

webはブラウザがローカルにストレージを持てるようになってから主流になってきた考え。

モバイルの利用時間が増えている。
ただし、オフラインになる時間も多く、利用者は結構当たり前で使えている。カコに表示したデータは保持しているはず。。。

## 必要な機能

サーバとローカルのデータの同期をする必要性が出て来る。

### 通信

色々検討事項があり、かなりの複雑度になってしまう。

### DB

それぞれオンライン・オフライン用のロジックがあったり、複数の端末どうする？など。

### これらをRealm mobile platformが対応するよ

### Realm

使うかわからないObjectを遅延実行で初期化する

## CAP定理

Consistency
Abailabirity
COnsissso

---

目が痒くて集中出来ず。断念・・・。
聞いていた感想としては非常に便利な感じ。
問題はRealmのマイグレーションなどとかかな？
Q＆Aでもあったけど、両方残しつつ、新しい方には新規カラム追加とか。

---

Q 匿名ユーザ（ログインしていないユーザの場合の使い方）

A 例えばDroidkaigiのセッションのマスターデータをrealmでやりたいというようなケースの場合、それ用のユーザを作成し、それをみんなでつかうような形にすれば作成出来る。