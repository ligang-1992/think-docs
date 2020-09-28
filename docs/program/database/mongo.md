#### **2018-12-19	10:05**

#### 问题：数据库时间显示有时差

##### 解决方案：

###### 1、代码修改

```java
// 默认时间为格林威治时间，通过注解，修改时差 - "GMT+8" 
@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss") 
@JsonFormat(pattern = "yyyy-MM-dd HH:mm:ss", timezone = "GMT+8") 
private LocalDateTime time = LocalDateTime.now();
```

###### 2、有可能是可视化工具的问题，可视化工具设置显示本地时间

![mongo-time-option](mongo.assets/mongo-time-option.png)