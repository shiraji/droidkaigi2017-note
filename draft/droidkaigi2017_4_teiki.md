# 定期実行処理入門

フィードの更新とか今晩の9時に通知を送るとかとか。

# 実装方法どうする？ in 2017

## AlarmManager

* 古くから疲れており、枯れている。
* interfaceがシンプルで良い。
* OSによって挙動が違う
* 再起動時に消えるから再登録が必須
* 時間以外の制約が苦しい

AlarmManagerを使う実装が一番時間の厳密。
ただし、バッテリーくうよ。

## JobScheduler

Lollipopから登場の新しいAPI
Serviceを任意で起動。

クックパッド社でもこれを利用している。

### ツラいところ

N未満はバグがある。ただし、Deadlineを長くすれば問題ないよ。

再現性がないが、何十倍の起動をする端末がある。
  チェック機構を設けたほうが良い。

## GCMNetworkManager

JobScheduleと同様？

将来性が若干イマイチわからない。

## Firebase JobDispatcher

こいつがいるので、GCMNetworkManagerが若干微妙。
コードが公開されていて、

## GCM

play serviceに対してIntentを投げて、条件を満たした場合、intent-filterを通じて呼び出す。

Firebase周りを利用してServiceを起動。

## その他

androi-job/Evernote 4.0+。闇を吸収
SyncAdapter

