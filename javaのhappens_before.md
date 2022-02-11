%:20210211

* 動画: https://www.youtube.com/watch?v=oY14UyP61F8
* text: http://tutorials.jenkov.com/java-concurrency/java-happens-before-guarantee.html
* syncronizedキーワードを入れることで、

## volatile keyword
 http://tutorials.jenkov.com/java-concurrency/java-happens-before-guarantee.html
### volatile変数へのwrite 
* volatile変数にwriteする時、その変数への書き込みは即座に(atomicに)memoryに反映されることが保証される
* また、他のthreadに公開している、non volatileな変数もmemoryにflushされる(なぜ!？？？)

### volatile変数へのread
* readのときも、memoryから読むことが確約される
* さらに、non volatileな変数もmemoryから読まれる(なぜ？！)

## volatile変数のreorderingによるprogramの故障
```
// called by Frame producing thread
public void storeFrame(Frame frame) {
    this.frame = frame;
    this.framesStoredCount++;
    this.hasNewFrame = true;
}

// called by Frame drawing thread
public Frame takeFrame() {
    while( !hasNewFrame) {
        //busy wait until new frame arrives
    }

}
```
* hasNewFrameはvolatile変数
* 下のようにprogramを帰ると？？
```
public void storeFrame(Frame frame) {
    this.hasNewFrame = true;
    this.frame = frame;
    this.framesStoredCount++;
}
```
* hasNewFrameへの書き込みのタイミングで、frameとframesSoteCountがmain memoryに更新される(しかし、これは更新前の値である!!!!!!)
* そうすると、takeFrame()が新しい値を取得する前に終了する可能性がある。。。

## ここでjavaのheppens beforeの登場
* volatile変数周りでの不整合を防ぐのを目的とした、(主に)reorderingによる最適化に対する制約のこと
### volatileのwriteのhappens before制約
```
        // called by Frame producing thread
    public void storeFrame(Frame frame) {
        this.frame = frame;
        this.framesStoredCount++;
        this.hasNewFrame = true;  // hasNewFrame is volatile
    }
```
* 上の例において、volatileより先にprogram上で書かれた命令はreprderされない

### volatileのread
```
int a = this.volatileVarA;
int b = this.nonVolatileVarB;
int c = this.nonVolatileVarC;
```
* 2,3行目が1行目より前にorderされることがない
* 2,3行目同士は自由にorderingできる

## javaのSynchronized
* 基本的にはvolatileに近い感じ
* blockに囲まれた処理は単独のthreadが(atomicではないと思うが)
* 

### javaのSynchronizedにenter
* 他のthreadに晒してる変数をmemoryから読んでreflash
### javaのSynchronizedからexit
* 変数をmemoruにflush

### 利点
* 上記を実施することで、syncronized blockの処理をthread1が行った後にthread2が行った際にthread1がobjectに行った変更は、thread2が開始されたタイミングでは絶対に反映されている

### 例
```
public class ValueExchanger {
    private int valA;
    private int valB;
    private int valC;

    public void set(Values v) {
        this.valA = v.valA;
        this.valB = v.valB;

        synchronized(this) {
            this.valC = v.valC;
        }
    }

    public void get(Values v) {
        synchronized(this) {
            v.valC = this.valC;
        }
        v.valB = this.valB;
        v.valA = this.valA;
    }
}
```
* getterは最新の値を使いたいのであれば、methodの頭にsyncronized blockをおく
* setterは最新の値をflushさせたいなら、methodの後ろにsncronizedをおく


### その他
* volatileとsyncronizedの違い
  * volatileはつまるところatomic変数を宣言(変数へのread, writeは即座にmemoryから取得 or flushされる)してること？
  * syncronizedは、引数に渡したobjectに対するlockを獲得するimage?(block内に記述した処理のatomicな操作は提供しているわけではない)
* volatileの落とし穴
  * volatileは変数のlockを取ってるわけではないので、counterのincrementみたいな複数操作にまたがる(read単体、write単体ではなく)操作には適しない.
    * https://stackoverflow.com/questions/3519664/difference-between-volatile-and-synchronized-in-java#:~:text=Effectively%2C%20a%20variable%20declared%20volatile,overhead%20than%20%22plain%22%20variables.
    * https://www.javamex.com/tutorials/synchronization_volatile.shtmlc 