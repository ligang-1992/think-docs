#### 反射

> Java反射机制是指在运行状态下，对于任意一个类，都能知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性。
>

###### 1.1	Java反射机制主要提供了一下功能：

1. 在运行时判断任意一个对象所属的类
2. 在运行时构造任意一个类的对象
3. 在运行时判断任意一个类所具有的成员变量和方法
4. 在运行时调用任意一个对象的方法
5. 生成动态代理

#### 代理

###### 1.1	静态代理：

> 静态代理需要为每一个具体的类都完成一个代理类。
>

###### 1.2	动态代理：

> 动态代理是动态地生成具体委托类的代理类实现对象，不需要为各个委托类逐一实现代理类，只需要为一类代理行为写一个具体的实现类就行了。
>

#### Time

```json
				{
            // 获取当天日期
            LocalDate today = LocalDate.now();
            System.out.println("今天的日期是： " + today);
        }

        {
            LocalDate today = LocalDate.now();
            int year = today.getYear();
            int month = today.getMonthValue();
            int day = today.getDayOfMonth();
            System.out.println("年：" + year + "\n月：" + month + "\n日：" + day);
        }

        {
            LocalDate dateOfBrith = LocalDate.of(2019, 5, 23);
            System.out.println("日期：" + dateOfBrith);
        }

        {
            LocalDate date = LocalDate.of(2019, 5, 23);
            LocalDate day = LocalDate.now();
            System.out.println("今天的日期是2019-5-23? " + day.equals(date));
        }

        {
            // 获取当前时间
            LocalTime localTime = LocalTime.now();
            System.out.println(localTime);
        }

        {
            LocalTime localTime = LocalTime.now();
            System.out.println("现在的时间是：" + localTime);
            LocalTime two = localTime.plusHours(2);
            System.out.println("两个小时后的时间：" + two);
        }

        {
            Instant timestamp = Instant.now();
            System.out.println("当前的时间戳是：" + timestamp);
        }
```

### 线程

#### 1	线程的创建

```java
// 1、继承java.lang.Thread, 重写run()方法
public class TestThread extends Thread {
    @Override
    public void run() {
        // 线程业务处理
    }
  
  	public static void main(String[] args) {
        TestThread test = new TestThread();
        test.start();
    }
}

// 2、实现java.lang.Runnable接口，重写run()方法，然后使用Thread类来包装
public class TestThread implements Runnable {
    @Override
    public void run() {
         // 线程业务处理
    }
  
  	public static void main(String[] args) {
        TestThread test = new TestThread();
        new Thread(test).start();
    }
}

// 3、实现Callable接口，重写call()方法，然后包装成java.util.concurrent.FutureTask, 再然后包装成Thread
public class TestCallable implements Callable<Boolean> {
    
    @Override
    public Boolean call() throws Exception {
				// 线程业务处理
      
      	// 返回值
        return true;
    }

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        TestCallable test = new TestCallable();

        // 创建执行服务
        ExecutorService service = Executors.newFixedThreadPool(3);

        // 提交执行
        Future<Boolean> future = service.submit(test);

        // 获取结果
        Boolean result = future.get();

        // 关闭服务
        service.shutdown();
    }
}

```

#### 2	锁

#### 2.1	死锁

###### 2.1.1	死锁的发生必须具备以下四个[必要条件]

1. 互斥条件：指进程对所分配到的资源进行排它性使用，即在一段时间内某资源只由一个进程占用。如果此时还有其它进程请求资源，则请求者只能等待，直至占有资源的进程用毕释放。

2. 请求和保持条件：指进程已经保持至少一个资源，但又提出了新的资源请求，而该资源已被其它进程占有，此时请求进程阻塞，但又对自己已获得的其它资源保持不放。

3. 不剥夺条件：指进程已获得的资源，在未使用完之前，不能被剥夺，只能在使用完时由自己释放。

4. 环路等待条件：指在发生死锁时，必然存在一个进程——资源的环形链，即进程集合{P0，P1，P2，···，Pn}中的P0正在等待一个P1占用的资源；P1正在等待P2占用的资源，……，Pn正在等待已被P0占用的资源。

