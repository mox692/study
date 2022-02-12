## test and set
* HWレベルでsupportされてる、atomic命令について見ていく


## CAS (compare and swap)
* https://ja.wikipedia.org/wiki/%E3%82%B3%E3%83%B3%E3%83%9A%E3%82%A2%E3%83%BB%E3%82%A2%E3%83%B3%E3%83%89%E3%83%BB%E3%82%B9%E3%83%AF%E3%83%83%E3%83%97
```
function cas(p: pointer to int, old: int, new: int) is
    if *p ≠ old
        return false

    *p ← new

    return true

```
* Maurice Herlihy (1993年) は、CAS命令が単なるリード、ライトやテスト・アンド・セットでは実装できないことを示した[1]
* なんで、casはtest and setとは独立(重複していない)と言える
* 

## TASとCASノチガイ
* https://stackoverflow.com/questions/3659336/compare-and-swap-vs-test-and-set
  * 一方で他方を表現できないっぽいな