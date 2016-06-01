# 欢迎来到 Swift 算法俱乐部！

在这里，你可以找到很多流行的算法和数据结构的具体实现，使用的是大家最喜欢的新语言 Swift，并对他们的工作原理配有详细的解释。

如果你是一个计算机学院的学生，为了考试想学习一下算法；又或者你是一个自学成才的程序员，想提高一下自身的理论姿势水平－－你真 TM 来对地方了！

这个项目的目的是**解释各种算法的工作方式**。所以我们主要关注代码的清晰性和可读性，而不是为了产出一个可复用的库，让读者可以直接拖进自己的工程使用。换句话说，绝大多数的代码都是可以用于实际的项目中的，不过需要你根据自己的项目需求进行一些修整。

所有的代码都是兼容 **Xcode 7.3** 以及 **Swift 2.2** 的。如果 Swift 有更新，我们也会及时跟进。

这个项目目前正在进行中。更多的算法将被加入，敬请期待。:-)

:heart_eyes: **欢迎提供建议和贡献！** :heart_eyes:

## 重要链接

[什么是算法和数据结构？](What are Algorithms.markdown) 薄饼！

[为什么要学习算法？](Why Algorithms.markdown) 还在担心这不是你的菜吗？请读一下这篇文章。

[Big-O 标记](Big-O Notation.markdown)。 我们经常会听到这样的话：“这个算法是 O(n) 的”。如果你不知道这是啥意思，请读读这篇文章。

[算法设计技巧](Algorithm Design.markdown)。 怎样设计自己的算法？

[参与进来！](How to Contribute.markdown)开个 issue 反馈一下你的想法，或者提交一个 pull request。

## 从哪开始？

如果你之前没有接触过算法和数据结构，你可以从下面这些简单易懂的算法开始看起：

- [栈](Stack/)
- [队列](Queue/)
- [插入排序](Insertion Sort/)
- [二分搜索](Binary Search/)和[二分搜索树](Binary Search Tree/)
- [归并排序](Merge Sort/)
- [Boyer-Moore 字符串搜索算法](Boyer-Moore/)

## 算法列表

### 搜索算法

- [线性搜索](Linear Search/)。从数组中查找某个元素。
- [二分搜索](Binary Search/)。从已排序的数组中快速查找元素。
- [统计出现次数](Count Occurrences/)。统计某个值在数组中的出现次数。
- [查找最大／最小值](Select Minimum Maximum)。找到数组中的最大／最小值。
- [第 K 大元素](Kth Largest Element/)。找到数组中的第 **K** 大元素，例如中位数。
- [选取样本](Selection Sampling/)。随机地从集合中选取一些元素作为样本。
- [并查集](Union-Find/)。保持一些不相交的集合，帮助你快速合并它们。

### 字符串搜索算法

- [Brute-Force 算法](Brute-Force String Search/)。一个简单粗暴的方法。
- [Boyer-Moore 算法](Boyer-Moore/)。一种高效的字符串子串搜索算法。它不需要对被搜索的字符串中的字符进行逐一比较，而是根据一个查找表跳过其中的某些部分。
- Rabin-Karp 算法
- [最长公共子序列算法](Longest Common Subsequence/)。找到两个字符串中的最长公共子序列。

### 排序算法

探究排序算法的工作原理是非常有趣的，但在实际的编码中，你几乎永远也不会需要自己编写排序算法，Swift 自带的 `sort()` 函数已经非常够用了，但如果你还是好奇背后的原理，请继续阅读。

基本的排序算法：

- [插入排序](Insertion Sort/)
- [选择排序](Selection Sort/)
- [希尔排序](Shell Sort/)

快速的排序算法：

- [快速排序](Quicksort/)
- [归并排序](Merge Sort/)
- [堆排序](Heap Sort/)

特殊的排序算法

- [桶排序](Bucket Sort/) :construction:
- [计数排序](Counting Sort/)
- 基数排序
- [拓扑排序](Topological Sort/)

不好的排序算法（知道就行了，不要用！）：

- [冒泡排序](Bubble Sort/)

### 压缩算法

- [变动长度编码法(RLE)](Run-Length Encoding/)。将重复的值存储为一个单字节及其计数。
- [哈夫曼编码](Huffman Coding/)。将常见的元素使用更小的单位存储。

### 杂项

- [搅乱算法](Shuffle/)。随机搅乱数组中的内容。

### 数学向算法

- [最大公约数算法(GCD)](GCD/)。特殊福利：最小公倍数算法。
- [排列组合算法](Combinatorics/)。还记得高中学过俄组合数学吗？
- [调度场算法](Shunting Yard/)。用于将中缀表达式转换为后缀表达式的经典算法。
- 统计算法

### 机器学习

- [k-Means 聚类算法](K-Means/)。无监督的分类器，将数据聚类为 K 个簇。
- K-近邻算法
- 线性回归
- 逻辑回归
- 神经网络
- 网页排名算法

## 数据结构

对于特定的任务，数据结构的选择需要基于以下几点考量。

首先，你的数据是具有某种形态的，并且有一些必要的操作方法。如果你想基于关键字来查找对象，需要的是字典类型的数据结构；如果你的数据原生就是分层级的，就需要某种类型的树形结构；而如果你的数据是线性的，则你需要的是数据结构可能就是栈或队列等。

Second, it matters what particular operations you'll be performing most, as certain data structures are optimized for certain actions. For example, if you often need to find the most important object in a collection, then a heap or priority queue is more optimal than a plain array.



Most of the time using just the built-in `Array`, `Dictionary`, and `Set` types is sufficient, but sometimes you may want something more fancy...

### Variations on arrays

- [Array2D](Array2D/). A two-dimensional array with fixed dimensions. Useful for board games.
- [Bit Set](Bit Set/). A fixed-size sequence of *n* bits.
- [Fixed Size Array](Fixed Size Array/). When you know beforehand how large your data will be, it might be more efficient to use an old-fashioned array with a fixed size.
- [Ordered Array](Ordered Array/). An array that is always sorted.

### Queues

- [Stack](Stack/). Last-in, first-out!
- [Queue](Queue/). First-in, first-out!
- [Deque](Deque/). A double-ended queue.
- [Priority Queue](Priority Queue). A queue where the most important element is always at the front.
- [Bounded Priority Queue](Bounded Priority Queue). A queue that is bounded to have a limited number of elements. :construction:
- [Ring Buffer](Ring Buffer/). Also known as a circular buffer. An array of a certain size that conceptually wraps around back to the beginning.

### Lists

- [Linked List](Linked List/). A sequence of data items connected through links. Covers both singly and doubly linked lists.
- Skip List

### Trees

- [Tree](Tree/). A general-purpose tree structure.
- [Binary Tree](Binary Tree/). A tree where each node has at most two children.
- [Binary Search Tree (BST)](Binary Search Tree/). A binary tree that orders its nodes in a way that allows for fast queries.
- [AVL Tree](AVL Tree/). A binary search tree that balances itself using rotations. :construction:
- Red-Black Tree
- Splay Tree
- Threaded Binary Tree
- [Segment Tree](Segment Tree/). Can quickly compute a function over a portion of an array.
- kd-Tree
- [Heap](Heap/). A binary tree stored in an array, so it doesn't use pointers. Makes a great priority queue.
- Fibonacci Heap
- Trie
- B-Tree
- [Radix Tree](Radix Tree/) :construction:

### Hashing

- [Hash Table](Hash Table/). Allows you to store and retrieve objects by a key. This is how the dictionary type is usually implemented.
- Hash Functions

### Sets

- [Bloom Filter](Bloom Filter/). A constant-memory data structure that probabilistically tests whether an element is in a set.
- [Hash Set](Hash Set/). A set implemented using a hash table.
- Multiset
- [Ordered Set](Ordered Set/). A set where the order of items matters.

### Graphs

- [Graph](Graph/)
- [Breadth-First Search (BFS)](Breadth-First Search/)
- [Depth-First Search (DFS)](Depth-First Search/)
- [Shortest Path](Shortest Path %28Unweighted%29/) on an unweighted tree
- [Minimum Spanning Tree](Minimum Spanning Tree %28Unweighted%29/) on an unweighted tree
- [All-Pairs Shortest Paths](All-Pairs Shortest Paths/)

## Puzzles

A lot of software developer interview questions consist of algorithmic puzzles. Here is a small selection of fun ones. For more puzzles (with answers), see [here](http://elementsofprogramminginterviews.com/) and [here](http://www.crackingthecodinginterview.com).

- [Two-Sum Problem](Two-Sum Problem/)
- [Fizz Buzz](Fizz Buzz/)
- [Monty Hall Problem](Monty Hall Problem/)

## Learn more!

For more information, check out these great books:

- [Introduction to Algorithms](https://mitpress.mit.edu/books/introduction-algorithms) by Cormen, Leiserson, Rivest, Stein
- [The Algorithm Design Manual](http://www.algorist.com) by Skiena
- [Elements of Programming Interviews](http://elementsofprogramminginterviews.com) by Aziz, Lee, Prakash
- [Algorithms](http://www.cs.princeton.edu/~rs/) by Sedgewick

The following books are available for free online:

- [Algorithms](http://www.beust.com/algorithms.pdf) by Dasgupta, Papadimitriou, Vazirani
- [Algorithms, Etc.](http://jeffe.cs.illinois.edu/teaching/algorithms/) by Erickson
- [Algorithms + Data Structures = Programs](http://www.ethoberon.ethz.ch/WirthPubl/AD.pdf) by Wirth
- Algorithms and Data Structures: The Basic Toolbox by Mehlhorn and Sanders
- [Wikibooks: Algorithms and Implementations](https://en.wikibooks.org/wiki/Algorithm_Implementation)

Other algorithm repositories:

- [EKAlgorithms](https://github.com/EvgenyKarkan/EKAlgorithms). A great collection of algorithms in Objective-C.
- [@lorentey](https://github.com/lorentey/). Production-quality Swift implementations of common algorithms and data structures.
- [Rosetta Code](http://rosettacode.org). Implementations in pretty much any language you can think of.
- [AlgorithmVisualizer](http://jasonpark.me/AlgorithmVisualizer/). Visualize algorithms on your browser.

## License

All content is licensed under the terms of the MIT open source license.

[![Build Status](https://travis-ci.org/raywenderlich/swift-algorithm-club.svg?branch=master)](https://travis-ci.org/raywenderlich/swift-algorithm-club)
