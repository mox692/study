%Date%:20210217
%source%:https://isovalent.com/blog/post/2021-12-08-ebpf-servicemesh

* How eBPF will solve Service Mesh - Goodbye Sidecars
## 概要
* eBPFという機能を使って、sidecarから脱却しよう、という話
  * eBPF自体はkernelのプラグイン的なものをuserlandで作成できる技術みたいな認識をしていたけど、これがnetworkに応用されているみたい.

## 発見
* sidecarの場合は、外にtrafficを流す際に1つのVM上で `app -> kernel -> edge -> kernel -> internet` ってなってたが、eBPFを使うことでsidecarを経由せずにkernelに直接proxyを支援するcodeを入れることで app同士で通信できるようにする

* kernelに直接組み込まないのはなぜ？
  * kernelに機能を足すのはそもそもコストが高い
  * 現状はeBPFとしてkernel module的に組み込むことで使用されている

## 疑問
* sidecarのそもそもの仕組みがよくわかってない. (なんとなくコスト高いのは想像できるけども)

## その他
