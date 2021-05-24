## 算法复杂度

1.时间复杂度：运行所需时间

2.空间复杂度：运行所需空间

```c++
int a = 0. b = 0(两个单位的内存空间，故空间复杂度为O（1）# constant space complexity)
    
for (i = 0; i<N ;i++){# O((N)+O(N) = 2*O(N) 前面系数忽略，故为O(N)）
    a = a + rand(); # 一个操作执行N次，故有N*1个操作，时间复杂度为O(N)
    b = b + rand(); # O(N)
}
for(j = 0; j<N; j++){
    b = b + rand(); # N/2 *1个操作 = 1/2 * O(N) = O(N) 
}
ps:若复杂度为C*O(N),若C为与N无关的数，则复杂度可写为O（N）
```



```c++
int a = 0, i, j
for(i = 0; i < N; i++){
    for(j = N; j>i; j--){
        a = a + i + j;
    }
}
# 时间复杂度：O(N^2);
# 空间复杂度：O(1)
```



```c++
int a = 0, i = N;
while (i>0) {
    a += i; #1个操作
    i /= 2; #1个操作
}

设N = 40； i =40，则：
i=20    2（操作数）
i=10    2 
i=5     2
i=2     2
i=1     2
i=0     2
    
操作数：2*6（N=40时），若操作数为N,则时间复杂度为2*O(log N) = O(log N)
```



算法X效率高于算法Y：指时间复杂度 X>Y

若用秒来计算，x的实际效率不一定高于Y

n足够大时可以保证x>y

![img](https://pic4.zhimg.com/80/v2-f2c2749d626c958eed7c320a10930f57_720w.jpg)



![img](https://pic3.zhimg.com/80/v2-e879535dab892ff8458d85bb5ff3648a_720w.jpg)



ps:指数级最复杂



## 主定理计算递归式算法的时间复杂度


$$
T(n) = aT(N/b)+f(n)
$$

- ![[公式]](https://www.zhihu.com/equation?tex=n) 是问题规模大小；
- ![[公式]](https://www.zhihu.com/equation?tex=a) 是原问题的子问题个数；
- ![[公式]](https://www.zhihu.com/equation?tex=n%2Fb) 是每个子问题的大小，这里假设每个子问题有相同的规模大小；
- ![[公式]](https://www.zhihu.com/equation?tex=f%28n%29) 是将原问题分解成子问题和将子问题的解合并成原问题的解的时间。



对上面的式子进行分析，得到三种情况：

![image-20210524122546269](C:\Users\。\AppData\Roaming\Typora\typora-user-images\image-20210524122546269.png)

计算复杂度步骤：

1.计算m =![image-20210524122816527](C:\Users\。\AppData\Roaming\Typora\typora-user-images\image-20210524122816527.png)

2.比较m与f(n)大小,根据情况套用复杂度公式

m > f(n): case 1

m = f(n): case 2

m < f(n): case 3

ps:第二种情况中k的确定：f(n)与原始比较确定



记忆：谁大取谁（m与f(n)）,相等定k