%Date%:20220514
%source%:https://hashrust.com/blog/moves-copies-and-clones-in-rust/

## 概要

## 発見
* moveの時にstack上で起こるcopyはshallow copyであり、データを複製するC++とは別の仕組み
* *This change of ownership is good because if access was allowed through both v and v1 then you will end up with two stack objects pointing to the same heap buffer:*
  * 間違いない.
* When a value is moved, Rust does a shallow copy; 
  * 一般にこう言えそうかな
    * stackを指してるデータは、って感じかな
* copyを実装しているObjectの代入(=)は、stack上に完全なる複製を作成する.
  * これはほとんど意識してなかったな-----
* 同じものを参照していない(完全に別物)なので、borrow errorが起きない.
* *In general, any type that implements Drop cannot be Copy because Drop is implemented by types which own some resource and hence cannot be simply bitwise copied. But Copy types should be trivially copyable. Hence, Drop and Copy don't mix well.*
  * ここがちょっとよくわかんない 

## 疑問

## その他
