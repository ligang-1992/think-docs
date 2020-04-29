#### Thread的几个常用方法的介绍

##### 1. Thread.yield()

使当前线程从**执行状态（运行状态）变为可执行态（就绪状态）**，为同一个优先级的线程让位，但是让位时间不确定。cpu会从众多的可执行态里选择，也就是说，**当前也就是刚刚的那个线程还是有可能会被再次执行到的**，并不是说一定会执行其他线程而该线程在下一次中不会执行到了。

```
public class MultiWrite {

    static int a = 0;

    public static void main(String[] args) throws Exception {
//        for (int i = 0; i <10 ; i++) {
//            new Thread(()->a +=1).start();
//        }
        Thread t = new Thread(() -> System.out.println(a = 1));
        //必须先开启线程，再执行join方法
        t.start();
       
        Thread.currentThread().yield();
        System.out.println(a);

    }
}
```

可能出现1,0和0,1的情况

##### 2. Thread.join()

把指定的线程加入到当前线程中，可以将两个交替执行的线程合并为顺序执行的线程。
比如在B线程中执行线程A的join方法，a.join(),**那么B线程就会暂停执行，先等A线程执行完毕，B线程再重新进入可运行状态**。

join方法中还可以设置时间a.join(1000),这样就让A执行规定时间。

```
public class MultiWrite {

    static  int a = 0;

    public static void main(String[] args) throws Exception{
//        for (int i = 0; i <10 ; i++) {
//            new Thread(()->a +=1).start();
//        }
        Thread t = new Thread(() -> System.out.println(a=1));
        //必须先开启线程，再执行join方法
        t.start();
        t.join();
        System.out.println(a);

    }
}
```

打印出1,1

作者：ZMRWEGo
链接：https://www.jianshu.com/p/92cb3b893c7b
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

