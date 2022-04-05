%Date%:20210217
%source%:https://prog-lang-sys-ja.slack.com/archives/CK1JKHYS1/p1645013224745959

## 概要
* indexの本質に土え考える
## 発見
* indexは、あるtableに対してあるクエリを実行したいときに、そのクエリが素早く実行されるように下準備を施しておくことに相当する.

### 例
```
| uid | name | age |
| 1   | "adf"| 33  |
| 2   | "erw"| 12  |
| 3   | "3rw"| 1   |
| 4   | "e41"| 52  |
```
 上のtableに対していろんな検索を考えてみる
#### case1: `select * where uid = 3`
* tableがbtreeで保存されてるのだとすれば、そのbtreeのデータ構造を使って一瞬で検索できそう

#### case2: `select * where age = 44
* 特にindexがなければ上から順に実行されてO(n)の計算量が発生しそう?
* indexが貼られていたら、それなりに速そう

## 疑問

## その他
