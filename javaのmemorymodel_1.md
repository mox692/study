%Date%:20210220
%source%:http://tutorials.jenkov.com/java-concurrency/java-memory-model.html

## 概要
* javaのメモリモデルの概説

## 発見
### The Internal Java Memory Model
* Each thread running in the Java virtual machine has its own thread stack. 
  * やはり、JVM内のthreadは独自のmemory領域を持ってるみたい
* Even if two threads are executing the exact same code, the two threads will still create the local variables of that code in each their own thread stack.Thus, each thread has its own version of each local variable.
  * やはり、決定的
* One thread may pass a copy of a pritimive variable to another thread, but it cannot share the primitive local variable itself.
  * 「thread localな変数のcopyを渡す」ということはできるが、「local変数自体を共有する」ことはできない
* The heap contains all objects created in your Java application, regardless of what thread created the object.
  * heapっていう領域もあって、これはthread stackとは別の概念
* The heap contains all objects created in your Java application, regardless of what thread created the object.
  * heapにはJVM上で作られた全ての変数が格納されてるみたい
* An object may contain methods and these methods may contain local variables. These local variables are also stored on the thread stack, even if the object the method belongs to is stored on the heap.
  * *(heap上にある)objectはmethodを保有することがあり、さらにそのmethod自体がlocal変数を保有している場合があります.そのlocal変数を保有してるmethodがheap上にあったとしても、これらのlocal変数はthread stackに保存されます*
  * ↑まじかw結構複雑
* Objects on the heap can be accessed by all threads that have a reference to the object. When a thread has access to an object, it can also get access to that object's member variables. If two threads call a method on the same object at the same time, they will both have access to the object's member variables, but each thread will have its own copy of the local variables.

### Hardware Memory Architecture
* The values stored in the cache memory is typically flushed back to main memory when the CPU needs to store something else in the cache memory. 
  * cache -> main memory へのflushっていう観点は確かに抜けてたな。これはどういう順番で行ってるのだろう

### Bridging The Gap Between The Java Memory Model And The Hardware Memory Architecture
* On the hardware, both the thread stack and the heap are located in main memory.Parts of the thread stacks and heap may sometimes be present in CPU caches and in internal CPU registers. 
  * なるほど. JVMのthreadもheapも、hardからしたら、全てmain memory上にあるようにしかいめない(それが時々、cacheニノって辺り、registerに乗ってたりするかも)
* When objects and variables can be stored in various different memory areas in the computer, certain problems may occur. The two main problems are:
  * Visibility of thread updates (writes) to shared variables.
  * Race conditions when reading, checking and writing shared variables.

#### Visibility of Shared Objects
* 簡単にいうと、「共有変数をwriteした際の変更がcpu localなキャッシュにしか残らず、その変更を他のcpuが確認できないタイミングが存在してしまう」

#### Race Conditions
* 複数処理をatomicに実行する仕組みがないと、意図してない不便な状況が発生することがある(本文の例を参考に。)

## 疑問

## その他