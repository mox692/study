%Date%:20210301
%source%:

## 概要

* 下記を解きたい
  * fileシステムとはなにか？
    * 恐らく、disk上にデータを保存したり取得するための仕組みを提供してるもの
    * disk上に散乱してるように見えるデータも、filesystemの定義に従ってやると、読めたり書けたりするイメージ
  * どういう用件が求められる？ 
    * まずはシンプルに考えると、
      * 新しく書き込まれた順にdiskの先頭から書いていく
      * ただし、kernel側は、特定の位置に何が保存してあるかを人間が読める形に変換する必要があるので、diskに保存する形式にそのような変換が可能な形式を選ぶ必要がある.
      * 例えば、1つのfileのサイズをdisk上の100byteに限定してしまって、| file名(10byte) | path(10byte) | data(80byte) | みたいにしてしまう方法も考えられる.
    * パフォーマンスを出すためには、
      * diskの特性を加味する必要がありそう
  * inodeとはなにか
  * ファイルアクセスするときに、kernelはどのように動く？

* https://www.youtube.com/watch?v=6KjMlm8hhFA
* https://stackoverflow.com/questions/347620/where-are-all-my-inodes-being-used
* https://stackoverflow.com/questions/25819226/what-is-the-difference-between-inode-number-and-file-descriptor

* ここ読むのが一番強い気がしてきた
  * https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout
  * https://en.wikipedia.org/wiki/Inode
  * source 
    * https://www.reddit.com/r/linux4noobs/comments/jhwqq5/how_do_you_explain_inodes_better/
## 発見

* なんか最近勉強してるDB関連の話と通じるものがすごくありそう
  * 結局、「Userlandからのpahtを受け取って、disk上のデータを返す」って機構が基本だよね
## 疑問

## その他
