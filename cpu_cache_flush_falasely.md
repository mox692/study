%Date%:20210315
%source%:https://mechanical-sympathy.blogspot.com/2013/02/cpu-cache-flushing-fallacy.html

## 概要

## 発見
* *Memory Ordering Buffers (MOB)*
  * そもそも存在を初めて知った
  * L1 cacheの完了を待つ前に、store bufferを設けて、(storeした後の)先のReadの命令を実行してしまおうと言う考え方だと思う.
  * [ここ](https://keisanki.at.webry.info/201704/article_1.html)に書いてあるストアバッファが参考になった

## 疑問

## その他
