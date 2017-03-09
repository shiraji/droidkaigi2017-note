# RxJava2

スライド

https://speakerdeck.com/hkurokawa/whats-new-in-rxjava-2

# 変更点

Reactive Streamsという仕様に準拠した。AkkaとかReactiveのライブラリの人たちが集まって、その仕様を策定した。


# Reactive StreamsはBackpressureを導入した

が、Androidは2つのDataソースがあり、一つはコントロール出来る部分、もう一つはGUIのユーザイベント。
これはBufferにつめてもいいが・・・微妙。。。


# Rx2

## BPの違い

Backpressureありなしでクラス名が違う。表を参照。名前で明示するようになった。

## nullのハンドリング

nullは禁止。結構ここが大きな修正でもある。

## Single/Maybe/Completable

BPはないので、toListなどのオペレータはこれらを使うようになった。

## Performance向上

結構あがったよ！

## 以降する？

RxJavaは2018年3月まで！
どうせ移る必要があるならさっさと移行したほうがいいよ。

Action.Emptyはなくなっている。RxJava2Extensionsにある。
思想として、Rxは必要最低限しかないということから
