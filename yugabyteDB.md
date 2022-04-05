%Date%:20210217
%source%:https://blog.yugabyte.com/four-data-sharding-strategies-we-analyzed-in-building-a-distributed-sql-database/

## 概要
* シャーディングの戦略について
* 4つの手法が紹介されている

## 発見
* Algorithmic Sharding
  * キーをハッシュに変換して、それをノード数の余りで分散させるような仕組み
* デメリット
  * nodeを追加した時に、レコードが所属するnodeに変更が入る.結構変更が大きくなる
    * キャッシュの場合(実際にこれが使われてるのはredisとからしい)はmissするだけなのでまあ使いどころはある
* Linear Hash Sharding
  * シャードに一定の範囲をも足せる.ハッシュによる変換先は、そのシャードに(キーの順序を保ちつつ)良い感じに分散されるようにする.
  * デメリットとしては
    * シャードの範囲をどのように決定すれば良いのかを、事前に決めることが難しい
      * どのキーにどれくらいアクセスがくるか
      * 新しくnodeを追加する時、それに対応する新しいレコードにはどれくらいアクセスが来そうか

* Range Sharding
  * keyの範囲で絞り込むような、範囲検索のクエリには強いらしい？
  * [このビデオ](https://www.youtube.com/watch?v=avepna2q9w0)でなんとなくわかった
  * 

* Consistent Hash Sharding
  * nodeを追加した際にkeyの際割り当ての個数をなるだけ小さくするアルゴリズム
  * 参考
    * https://zenn.dev/tosa/articles/e9ce174c9d01ed
    * https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%B3%E3%82%B7%E3%82%B9%E3%83%86%E3%83%B3%E3%83%88%E3%83%8F%E3%83%83%E3%82%B7%E3%83%A5%E6%B3%95

## 疑問
* シャードってレコードを分割するんじゃなくて、行を別のnodeに置く話だったのか
  * 勘違いしてた。水平分割がshardingらしい
    * https://medium.com/teamgeekhash/sharding-%E3%81%A8%E3%81%AF-7731655b0391

## その他
* シャーディングのデメリット、ここの記事良かった
  * https://pecopla.net/web-column/db-shard
