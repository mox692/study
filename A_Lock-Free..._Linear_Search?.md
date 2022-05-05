%Date%:20220502
%source%:https://preshing.com/20130529/a-lock-free-linear-search/

## 概要

## 発見
### Atomicity
* *all modern CPUs, a plain, natively-aligned 32-bit assignment is already atomic.*
  * あれ、そうなの？
  * そのあとrに *if these were 64-bit integers, a plain assignment on x86 would most definitely not be atomic.* ってかいてあるから、32bitのstoreはatomicが保証されてるのかな
  * [この辺](https://stackoverflow.com/questions/49989123/atomicity-of-32bit-read-on-multicore-cpu)にも書いてあっった
    * 確かに32bitと64bitではちょっと話が違いそう
  * *More importantly, when several threads are hammering on the same variable, they will all line up in a row and execute the CAS one-at-a time, resulting in a single, global order of all CAS operations (indeed, all RMW operations) on that variable.*
    * ここが理解できればこの記事は大体クリアできている気がしてくるね.
    * 複数スレッドから同時に操作があっても、CASの性質からそれが直列で実行されているのち意味的におなz

## 疑問

## その他
