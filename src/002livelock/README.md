## 活锁
两个或两个以上的并发协程试图在没有协调的情况下防止死锁。
这就好比，走廊里有2个人相遇，互相给对方让路，你让我，我让你，最后2个人都不能往前走。

## 执行结果
```text
Apple is trying to scoot: left right left right left right left right left right
Apple tosses her hands up in exasperation!
Banana is trying to scoot: left right left right left right left right left right
Banana tosses her hands up in exasperation!
```
or
```text
Banana is trying to scoot: left right left right left right left right left right
Banana tosses her hands up in exasperation!
Apple is trying to scoot: left right left right left right left right left right
Apple tosses her hands up in exasperation!
```
开了2个goroutine执行walk，谁先谁后不确定，所以会有2种不同的结果。