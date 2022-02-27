%Date%:20210227
%source%:https://prog-lang-sys-ja.slack.com/archives/CK1JKHYS1/p1645013224745959

## 概要
* issue
  * https://github.com/rust-lang/rust/issues/93448
  
## 情報収集
* terminationのdocs
  * https://doc.rust-lang.org/beta/std/process/trait.Termination.html#tymethod.report
* これらはsourceからbuildされている？
  * library/std/src/process.rsに、コメントがある
  * ここも同様に https://doc.rust-lang.org/std/ops/trait.Deref.html
* termination関連のRFC
  * https://github.com/rust-lang/rust/issues/43301
* その他のdocs関連のissue
  * https://github.com/rust-lang/rust/issues/89175
* docsのexampleが分かりにくすぎるから、contributeしたったわ、ってやつ
  * https://github.com/rust-lang/rust/pull/93851

## issueに関連するもの
### RFC
* https://github.com/rust-lang/rfcs/pull/1937

### issue トラッカ
* https://github.com/rust-lang/rust/issues/43301

### 関連PR, issue
* https://github.com/rust-lang/rust/pull/93840
* https://github.com/rust-lang/rust/issues/43301
* [main in nostd environments](https://github.com/rust-lang/rfcs/blob/master/text/1937-ques-in-main.md#main-in-nostd-environments)
  * https://internals.rust-lang.org/t/allowing-for-main-to-be-divergent-in-embedded-environments/4717

## 疑問
* issueに取り組むために必要な具体的な手順
  * terminateに関する具体的な情報収集.

## その他
* PRは [こんな感じ](https://github.com/rust-lang/rust/pull/93956) でまとめてmergeされるみたい