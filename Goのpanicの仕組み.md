%Date%:20220305
%source%:

## 概要
* Go改造計画として、panicの仕組みを追ってみる.

## memo
* ランタイムのどっかでSIGSEGV を発生してるみたい 
* error文
```
invalid memory address or nil pointer dereference [signal SIGSEGV: segmentation violation]
Unable to propagate EXC_BAD_ACCESS signal to target process and panic
```


## 作業stack
* ひたすらコードだけを追う
* comment読む
* panicの実装がどっかでされてるハズ？

## 疑問
* 

## 参考資料
* https://developpaper.com/detailed-explanation-of-golang-panic/
  * panicの実装についてかなり細かく書いてあてよい
