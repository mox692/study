%Date%:20210217
%source%:https://prog-lang-sys-ja.slack.com/archives/CK1JKHYS1/p1645013224745959

## ことの発端
* https://prog-lang-sys-ja.slack.com/archives/CK1JKHYS1/p1645013224745959
  * ここで投げた質問.いろんな方に回答いただいた
  
## 内容
* どのようにmemoryにデータを配置すればキャッシュヒットしやすい？

## 結論
* 基本的には返事いただいた内容全部が参考になる(ありがたい。。。)
* 基本的には「アクセスするデータにメモリアドレスがどのように割り当たって、どういうアドレスパターンでアクセスするか」だけが問題
* ただし、「どのように割当たって」の部分は「処理系(コンパイラ)」や「ランタイム(jit)」に大きく依存しうるので、一概にこのようにコードを書いたらキャッシュヒットしやすいなどは言えない
* 例えば、処理する内容によっては、SoAの方が速い場合もある
  * https://stackoverflow.com/questions/17924705/structure-of-arrays-vs-array-of-structures
* キャッシュの話をもう一回復習したいな
