%Date%:20210315
%source%:https://mechanical-sympathy.blogspot.com/2012/08/memory-access-patterns-are-important.html

## 概要

## 発見
* 記事内に、具体的なコードと、実行速度が書いてあったので、それだけですでに有用な記事.
* どのprocessorでも、cache外す(random walk)と10倍くらい(linear walkと比較して)遅くなることがわかった.
* ただ、それ以外は結構すでに読んだmemory model系の記事に近いしい内容のものだった(russ, java)

## 疑問
* page walk -> pageないのメモリアクセス
* heap walk -> (pageを跨ぎうる)memory領域へのアクセスのこと？

## その他
