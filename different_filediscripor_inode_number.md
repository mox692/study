%Date%:20210217
%source%:https://www.quora.com/Whats-the-difference-between-inode-number-and-file-descriptor

## 概要
* inode numberとfile discriptro numebrの違い

## 発見
* inode
  * filesystem上のpointer的なもの
  * 必ずdevice上に保存されてるデータに関連している
  * そのデータが使用されてなくても、inode番号はある
* filediscriptor
  * processごとに用意される、ファイルの識別子
  * 必ずしもdevice上に保存されてるdataに限らない. socketや標準入出力に関してもfile discriptorが発行される
  * 使用していないファイルにはdiscriptrは発行されず、そのファイルがopenされてから初めてdiscriptorが割り当てられる.
## 疑問

## その他
