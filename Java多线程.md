# Java多线程

主要用到class中的Thread，interface中的Runnable。（位于java.lang包中）

Thread和Runnable中有共同的 public void run() 方法。提供了线程实际工作执行的代码

![1562576710102](C:\Users\E10S\AppData\Roaming\Typora\typora-user-images\1562576710102.png)

join()方法：等待当前线程执行完毕

## 正确停止线程

不能用 stop() 、interrupt()方法