%Date%:20210303
%source%:https://prog-lang-sys-ja.slack.com/archives/CK1JKHYS1/p1645013224745959

## 概要
* rustのinline asmが、書き方によってはgdbのstep実行で止まってくれなくなる

## 再現コード
* https://github.com/mox692/rust_inline_asm_search

## 考察
* asm!がどんなコードを履いてるか？
  * inline asmの構造を調べる
* デバッガ側がハンドルできない説も?
  * rust側は
* そもそもdebuggerってどうやって動くんだっけ?
  * step実行する仕組み

## 疑問

## その他
