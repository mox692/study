
%Date%:20210315
%source%:https://stackoverflow.com/questions/29796264/is-there-still-a-use-for-inline


## 概要

## 発見
* そもそもの前提
  * headerfileとは何者？
    * 単純に、プリプロセッサによって、プロトタイプ宣言を.cppに埋め込むために定義する
* それらを踏まえた上で
  * 課題
    * headerで定義した関数(実装つき)を複数のファイルでimportすると、複数definition errroになる.これはだるい.
    * inlineを使えば、そのキーワードを持った関数は複数の実装を持つことができる
    * つまり、headerで実装を定義して、それをcppで展開することができる
      * こういう意味において、inline キーワードがそのまま使われた?...
    * ~~ちなみに、inlineを使えば、同じシンボルで中身の実装が違うと言ったことも実現できる.(どっちが利用されるのかはよくわからん)~~
      * inline を使った関数は、C言語におけるglobal static変数的な扱いになるみたいで、file scopeになるっぽい
        * https://www.sejuku.net/blog/24205
      * なので、inline書かれた関数をlink時に参照しようとすると、できない
      * inlineはあくまで、link時に同じシンボルの関数定義が複数あってもerrorにしない機能、と言えそう.
## 疑問

## その他
