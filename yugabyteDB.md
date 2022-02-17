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

## 疑問
* シャードってレコードを分割するんじゃなくて、行を別のnodeに置く話だったのか
  * 勘違いしてた。水平分割がshardingらしい
    * https://medium.com/teamgeekhash/sharding-%E3%81%A8%E3%81%AF-7731655b0391

## その他
* シャーディングのデメリット、ここの記事良かった
  * https://pecopla.net/web-column/db-shard