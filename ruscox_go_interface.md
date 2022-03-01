%Date%:20210217
%source%:https://research.swtch.com/interfaces

## 概要
## 発見

* *Languages with methods typically fall into one of two camps: prepare tables for all the method calls statically (as in C++ and Java), or do a method lookup at each call (as in Smalltalk and its many imitators, JavaScript and Python included) and add fancy caching to make that call efficient. *
  * 両者の違いがいまいちわからん
  * 想像だけど「c++はコンパイル時にmethodのaddrが分かってる」「jsは実行しながらmethod tableを構築しつつ、methodが呼ばれた際は適宜そのtableを見にいく」
* *Note that the itable corresponds to the interface type, not the dynamic type.* 
  * これは何が言いたいのだろう
* *There's an obvious optimization when the value does fit in the slot; we'll get to that later.*
  * これはpointerを介した方がキャッシュhitが大きくなるから、ってこと？
* *The interface runtime computes the itable by looking for each method listed in the interface type's method table in the concrete type's method table.*
  * itableからその型のmethodoを抽出する方法に関して書いてある
  * 最初の1回目だけ、「型のmethod tableからinterfaceのmethodを探索する」という検索が必要になるが、それ以降はキャッシュして具象型 -> methodのaddrをすぐに探索できるようにsルウ
## 疑問

## その他
