#### 反射

​		Java反射机制是指在运行状态下，对于任意一个类，都能知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性。

###### Java反射机制主要提供了一下功能：

- 在运行时判断任意一个对象所属的类
- 在运行时构造任意一个类的对象
- 在运行时判断任意一个类所具有的成员变量和方法
- 在运行时调用任意一个对象的方法
- 生成动态代理

#### 代理

###### 静态代理：

​		静态代理需要为每一个具体的类都完成一个代理类。

###### 动态代理：

​		动态代理是动态地生成具体委托类的代理类实现对象，不需要为各个委托类逐一实现代理类，只需要为一类代理行为写一个具体的实现类就行了。

#### Time

```
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

