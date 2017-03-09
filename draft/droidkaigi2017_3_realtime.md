# リアルタイム通信アプリ

* 良い どんどん更新されていく
* 悪い 難しい。通信切れたり。

# WebSocket

okhttpのサポートが3.5.0でされた。

WebSocketはBinaryもサポートされている。しかも複合化とかしなくても問題ない。

デフォルトではbroadcastとかnamespace mechanizmすらない。軽くてすんごい薄い。
サーバの実装次第で結構やれる。

redisのpub/sub機能使うような方針も結構はまっている。

Offlineサポートなし

# Firebase(realtime dataase)

見た目上、ローカルだけど、後ろで動機が走っている

No SQLでJSONでのデータ構造

セキュリティの設定も簡単に出来る。

クライアントもOKボタン押していけば問題なし。

能動的にデータを取得するのは出来ない。

webhookはない

# Realm Mobile Platform

* Realm Mobile Database

ローカルのDB/ORM

Firebase Realtimeと同じようにRealmを使って、裏で同期される。

macOS/RHEL/Ubuntu/AWSのオンプレがある。開発版は無料。

Queryがわかりやすい

Pro版ならServer side hookあり

白山さんはRealm Mobile Platformが良いみたい。

