%Date%:20220505
%source%:https://qiita.com/qnighy/items/5b2fbf27e3ee36e57b8d

## 概要

## 発見
* *0やnullでない保証のある特別な型 (Box<T>, NonNull<T>, NonZeroU32 など) を Option で包んだときに None をnullと同一視することでサイズを削減する最適化が実装されています。*
  * これは全く知らなかったな...

## 疑問

## その他
