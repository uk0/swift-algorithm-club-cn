# 大 O 表示法  (A note on Big-O notation)

It's useful to know how fast an algorithm is and how much space it needs. This allows you to pick the right algorithm for the job.  
知道一个算法的运行时间和占用空间会非常有帮助, 能让你对要解决的问题选出正确的算法

Big-O notation gives you a rough indication of the running time of an algorithm and the amount of memory it uses. When someone says, "This algorithm has worst-case running time of **O(n^2)** and uses **O(n)** space," they mean it's kinda slow but doesn't need lots of extra memory.  
大 O 表示法能让你对一个算法的 运行时间(running time) 和 占用空间(amount of memory) 有个大概概念.  
当有人说 "这个算法在最糟情况下的运行时间是**O(n^2)** 而且占用了 **O(n)** 大小的空间 "   
他的意思是这个算法蛮慢的, 不过没占多大空间.   


Figuring out the Big-O of an algorithm is usually done through mathematical analysis. We're skipping the math here, but it's useful to know what the different values mean, so here's a handy table. **n** refers to the number of data items that you're processing. For example, when sorting an array of 100 items, **n = 100**.

要知道一个算法的大 O 表示法 通常要通过数学分析(mathematical analysis).   
我们这里跳过具体的数学, 不过知道不同的值意味着什么会很有用,  所以这里有一张方便的表.  
**n** 在这里代表的意思是数据的个数.  
举个例子, 当排序一个有 100 个元素的数组时, **n = 100**.

Big-O | 名字 | 描述
------| ---- | -----------
**O(1)** | 常数级(constant) | **最好.** 不论输入数据是多少, 这个算法的运行时间总是一样的.例子: 根据索引找出数组中对应的元素.
**O(log n)** | 对数级(logarithmic) | **相当好** 这种算法每次循环 (iteration) 的时候会把数据量减半. 如果你有 100 个元素 只需要 7 步就可以找到答案. 1000 个元素 只要 10 步.  1,000,000 元素只要 20 步. 即便数据量很大这种算法也非常快. 例子: 二分查找(binary search).
**O(n)** | 线性级(linear) | **好**  如果你有 100 个元素, 这种算法就要做 100 次工作. 数据量翻倍那么运行时间也翻倍. 例子: 线性查找(sequential search).
**O(n log n)** | 线性对数级(linearithmic) | **还行** 比线性级糟了一些, 不过也没那么差劲. 例子: 最快的通用排序算法(the fastest general-purpose sorting algorithms).
**O(n^2)** | 二次方级(quadratic) | **蛮慢的** 如果你有 100 个元素, 这个要做 100^2 = 10,000 次工作. 数据量 x2 会导致运行时间 x4 (因为2的2次方等于4). 例子: 循环套循环(nested loops)的算法, 比如插入排序(insertion sort)
**O(n^3)** | 三次方级(cubic) | **慢** 如果你有 100 个元素, 那么它要做 100^3 = 1,000,000 次工作=. 数据量 x2 会导致运行时间 x8.
例子: 矩阵乘法(matrix multiplication).
**O(2^n)** | 指数级(exponential) | **慢死了** 这种算法你要想放设防避免, 但有时候你就是没得选. 加一点点数据就会把运行时间成倍的加长. 例子: 旅行商问题(traveling salesperson problem).
**O(n!)** | 阶乘级(factorial) | **蜗牛慢** 不管干什么都要跑个 N 年才能得到结果  

Often you don't need math to figure out what the Big-O of an algorithm is but you can simply use your intuition. If your code uses a single loop that looks at all **n** elements of your input, the algorithm is **O(n)**. If the code has two nested loops, it is **O(n^2)**. Three nested loops gives **O(n^3)**, and so on.  
大部分情况下你用直觉就可以知道一个算法的大 O 表示法.  
如果你的代码用一个循环遍历你输入的每个元素, 那么这个算法就是 **O(n)**.  
如果是循环套循环, 那就是 **O(n^2)**.    
如果3个循环套在一起就是 **O(n^3)**, 以此类推   

Note that Big-O notation is an estimate and is only really useful for large values of **n**. For example, the worst-case running time for the [insertion sort](Insertion Sort/) algorithm is **O(n^2)**. In theory that is worse than the running time for [merge sort](Merge Sort/), which is **O(n log n)**. But for small amounts of data, insertion sort is actually faster, especially if the array is partially sorted already!  
注意大 O 表示法是一种估算, 当数据量大的时候才有用.   
举个例子, [插入排序](Insertion Sort/) 的最糟情况运行时间是 **O(n^2)**. 理论上来说它的运行时间比 [归并排序](Merge Sort/) 要慢.   
归并排序是 **O(n log n)**.  
但对于小数据量, 插入排序实际上更快一些, 特别是那些数组里已经有一部分数据是排序好了的.  

If you find this confusing, don't let this Big-O stuff bother you too much. It's mostly useful when comparing two algorithms to figure out which one is better. But in the end you still want to test in practice which one really is the best. And if the amount of data is relatively small, then even a slow algorithm will be fast enough for practical use.  
如果你看完没懂, 别太上心.  
当比较两种算法哪种好的时候 大 O 表示法 才有用.   
最后你总是希望实际测试哪个才是最好的.   
而且如果数据比较少, 哪怕算法比较慢, 实际使用也不会造成什么问题.    
