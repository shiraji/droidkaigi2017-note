# Performance

Easter Eggを参考に修正していく

## 一覧画面でANR

systrace - 特定の時間でどのスレッドでどの処理に時間がかかっているか判断出来る。

resourceファイルを読み込まれている処理が多い。

原因としては、餌を上げた時点で、ネコを描画処理が走っている。そのために発生したっぽい。

そこからデータが混合していることが問題と判断し、修正方法をそこに確定。
適切な処理に切り替えたらANR改善。

## スクロールのもたつき

Allocation Tracker(DDMS)

スタックトレースをたどることができて、呼び出し元がわかりやすい

重い描画処理を何度もしているので、そのあたりをチューニングしたっぽい？

DDMS
Leak Canary

その他

公式Ref

* Best Practices for Performance
* Profile Your App
