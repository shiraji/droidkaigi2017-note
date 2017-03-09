# Android Security 最前線！！

## Using Scoped Directory Access

ストレージの許可を出すと全てのストレージアクセスに許可できてた。

Android 7.0では特定のディレクトリへのアクセス権限のみ取得するようになった。

StorageVolume
StorageManager(StorageVolumeを取得するためのクラス)

primaryストレージかどうかの判別が必要。

## Direct Boot

Android6.0以前

端末が暗号化されている場合、data/userはロック解除された場合のみ利用できる。

アンロック前にダイレクトブートモードにアクセスすることも可能になった。
どういったデータの保存やデータ量を少なく？？？

BOOT_COMPLETEDは7.0でタイミングが変わったので注意。

# Network Security Config

カスタムCA証明書を信頼するための安全で簡単なAPIを提供
デフォルトではユーザが追加したCAは信頼されない。

証明書の追加は3種類。すでにあるやつ、アプリ内埋め込み、ユーザが入れる。

Debug用の証明書の設定も出来る。

usesClearTextTraffic=false

アプリ毎にCAを入れられるので、セキュリティ強化になっている。

Q 一つ目のStorageの件。Target SDKにしばられるのか？

A 古いアプリでも強制的に縛られる。

Q Direct Bootの保存するデータについて何かしらツールは？

A 今使っていない。Access Tokenを保存するにしても通常のAccess Tokenではなく、制限があるAccess Tokenなどで使う。
