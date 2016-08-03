# 插入排序

目标：将一个数组按照从低到高（或从高到低）来排序。

现有一个数字类型的数组需要进行排序，插入排序的工作方式如下：

- 首先，将这些待排序的数字放在一个数组中，成为未排序的原始数组。
- 从其中取出一个数字，具体取哪个无所谓。为简单起见，每次都直接取出第一个元素。
- 将这个数字插入到一个新的已排序数组中。
- 然后再次从未排序数组中取出一个数字，将其插入到已排序数组中。它要么插在第一个元素的前面，要么插在后面，来保证这两个数字是有序的。
- 再一次从未排序数组中取出一个元素，安插在新数组的合适位置，以求新数组依然有序。
- 一直这样做下去，直到未排序数组中没有数字了为止。这样就可以达到排序的目的了。

这就是算法叫“插入”排序的原因，因为排序过程中不断地从未排序数组中取出元素插入到已排序的目标数组。

*译者注：类似于打牌的时候抓牌的过程！*

## 举例

例如，待排序的数组为 `[ 8, 3, 5, 4, 6 ]`。

取出第一个数字 `8`，将它插入到已排序数组中。已排序数组目前还是空的，所以这个过程非常简单。已排序数组现在为 `[ 8 ]`，未排序数组为 `[ 3, 5, 4, 6 ]`。

取出下一个数字 `3`，将其插入到已排序数组。他应该在 `8` 的前面，所以已排序数组现在为 `[ 3, 8 ]`，未排序数组缩减为 `[ 5, 4, 6 ]`

取出下一个数字 `5`，将其插入到已排序数组中。它应该在 `3` 和 `8` 之间。所以，现在已排序数组为 `[ 3, 5, 8]`,未排序数组为 `[ 4, 6 ]`。

重复以上过程，直到未排序数组为空为止。

## 原地排序

根据上面的解释，排序过程中似乎使用了两个数组，一个用于存放未排序的的元素，另一个存放已排序的元素。

但实际上插入排序可以“原地”进行，无需再创建另一个数组。只需要标记好哪部分是未排序的，哪部分是已排序的即可。

初始数组为 `[ 8, 3, 5, 4, 6 ]`。我们使用 `|` 符号来分隔已排序和未排序部分：

	[| 8, 3, 5, 4, 6 ]

上图显示已排序部分为空，未排序部分的第一个数字为 `8`。

处理完第一个数字之后，数组如下所示：

	[ 8 | 3, 5, 4, 6 ]

目前，已排序的部分为 `[ 8 ]`，未排序的部分为 `[ 3, 5, 4, 6 ]`。分隔符 `|` 向右位移了一个单位。

下面列出了排序过程中数组内容的变化：

	[| 8, 3, 5, 4, 6 ]
	[ 8 | 3, 5, 4, 6 ]
	[ 3, 8 | 5, 4, 6 ]
	[ 3, 5, 8 | 4, 6 ]
	[ 3, 4, 5, 8 | 6 ]
	[ 3, 4, 5, 6, 8 |]

每一步分隔符 `|` 都向右位移一个单位。可以观察到，数组开头到分隔符之间的部分总是已排序的。未排序部分每减少一个元素，已排序部分就增加一个，直到未排序元素为空为止。

## 如何插入

每个周期开始，取出未排序数组的头部元素，将其插入到已排序数组中。这时候，必须要保证元素被插入到了正确的位置。怎么做呢？

现在假设已经完成了前面几个元素的排序，数组看起来像下面这样：

	[ 3, 5, 8 | 4, 6 ]

下一个待排序的数字是 `4`。我们要做的就是将其插入到已排序数组 `[ 3, 5, 8 ]` 的某个位置。

下面提供了一个实现思路：跟前面的元素 `8` 进行比较。

	[ 3, 5, 8, 4 | 6 ]
	        ^
	        
它比 `4` 大吗？是的，所以 `4` 应该放到 `8` 的前面去。我们将两个数字交换位置来达到目的：

	[ 3, 5, 4, 8 | 6 ]
	        <-->
	       已交换

至此还没有结束。交换之后，新的排在前面的元素 `5` 也比 `4` 大。我们如法炮制，也将这两个数字交换位置：

	[ 3, 4, 5, 8 | 6 ]
	     <-->
	    已交换

继续，再次检查排在前面的新元素 `3`，它比 `4` 大吗？不，它必 `4` 小，这就意味着 `4` 已经在正确的位置上了。已排序的数组也再次变得有序了。

这就是插入排序算法的内循环的文字描述了，具体的代码在下一节给出。通过交换数字的方式，我们将待排序的元素移动到了已排序数组的正确位置上。

## The code

Here is an implementation of insertion sort in Swift:

```swift
func insertionSort(array: [Int]) -> [Int] {
  var a = array                             // 1
  for x in 1..<a.count {                    // 2
    var y = x
    while y > 0 && a[y] < a[y - 1] {        // 3
      swap(&a[y - 1], &a[y])
      y -= 1
    }
  }
  return a
}
```

Put this code in a playground and test it like so:

```swift
let list = [ 10, -1, 3, 9, 2, 27, 8, 5, 1, 3, 0, 26 ]
insertionSort(list)
```

Here is how the code works.

1. Make a copy of the array. This is necessary because we cannot modify the contents of the `array` parameter directly. Like Swift's own `sort()`, the `insertionSort()` function will return a sorted *copy* of the original array.

2. There are two loops inside this function. The outer loop looks at each of the elements in the array in turn; this is what picks the top-most number from the pile. The variable `x` is the index of where the sorted portion ends and the pile begins (the position of the `|` bar). Remember, at any given moment the beginning of the array -- from index 0 up to `x` -- is always sorted. The rest, from index `x` until the last element, is the unsorted pile.

3. The inner loop looks at the element at position `x`. This is the number at the top of the pile, and it may be smaller than any of the previous elements. The inner loop steps backwards through the sorted array; every time it finds a previous number that is larger, it swaps them. When the inner loop completes, the beginning of the array is sorted again, and the sorted portion has grown by one element.

> **Note:** The outer loop starts at index 1, not 0. Moving the very first element from the pile to the sorted portion doesn't actually change anything, so we might as well skip it. 

## No more swaps

The above version of insertion sort works fine, but it can be made a tiny bit faster by removing the call to `swap()`. 

You've seen that we swap numbers to move the next element into its sorted position:

	[ 3, 5, 8, 4 | 6 ]
	        <-->
            swap
	        
	[ 3, 5, 4, 8 | 6 ]
         <-->
	     swap

Instead of swapping with each of the previous elements, we can just shift all those elements one position to the right, and then copy the new number into the right position.

	[ 3, 5, 8, 4 | 6 ]   remember 4
	           *
	
	[ 3, 5, 8, 8 | 6 ]   shift 8 to the right
	        --->
	        
	[ 3, 5, 5, 8 | 6 ]   shift 5 to the right
	     --->
	     
	[ 3, 4, 5, 8 | 6 ]   copy 4 into place
	     *

In code that looks like this:

```swift
func insertionSort(array: [Int]) -> [Int] {
  var a = array
  for x in 1..<a.count {
    var y = x
    let temp = a[y]
    while y > 0 && temp < a[y - 1] {
      a[y] = a[y - 1]                // 1
      y -= 1
    }
    a[y] = temp                      // 2
  }
  return a
}
```

The line at `//1` is what shifts up the previous elements by one position. At the end of the inner loop, `y` is the destination index for the new number in the sorted portion, and the line at `//2` copies this number into place.

## Making it generic

It would be nice to sort other things than just numbers. We can make the datatype of the array generic and use a user-supplied function (or closure) to perform the less-than comparison. This only requires two changes to the code.

The function signature becomes:

```swift
func insertionSort<T>(array: [T], _ isOrderedBefore: (T, T) -> Bool) -> [T] {
```

The array has type `[T]` where `T` is the placeholder type for the generics. Now `insertionSort()` will accept any kind of array, whether it contains numbers, strings, or something else.

The new parameter `isOrderedBefore: (T, T) -> Bool` is a function that takes two `T` objects and returns true if the first object comes before the second, and false if the second object should come before the first. This is exactly what Swift's built-in `sort()` function does.

The only other change is in the inner loop, which now becomes:

```swift
      while y > 0 && isOrderedBefore(temp, a[y - 1]) {
```

Instead of writing `temp < a[y - 1]`, we call the `isOrderedBefore()` function. It does the exact same thing, except we can now compare any kind of object, not just numbers.

To test this in a playground, do:

```swift
let numbers = [ 10, -1, 3, 9, 2, 27, 8, 5, 1, 3, 0, 26 ]
insertionSort(numbers, <)
insertionSort(numbers, >)
```

The `<` and `>` determine the sort order, low-to-high and high-to-low, respectively.

Of course, you can also sort other things such as strings,

```swift
let strings = [ "b", "a", "d", "c", "e" ]
insertionSort(strings, <)
```

or even more complex objects:

```swift
let objects = [ obj1, obj2, obj3, ... ]
insertionSort(objects) { $0.priority < $1.priority }
```

The closure tells `insertionSort()` to sort on the `priority` property of the objects.

Insertion sort is a *stable* sort. A sort is stable when elements that have identical sort keys remain in the same relative order after sorting. This is not important for simple values such as numbers or strings, but it is important when sorting more complex objects. In the example above, if two objects have the same `priority`, regardless of the values of their other properties, those two objects don't get swapped around.

## Performance

Insertion sort is really fast if the array is already sorted. That sounds obvious, but this is not true for all search algorithms. In practice, a lot of data will already be largely -- if not entirely -- sorted and insertion sort works quite well in that case.

The worst-case and average case performance of insertion sort is **O(n^2)**. That's because there are two nested loops in this function. Other sort algorithms, such as quicksort and merge sort, have **O(n log n)** performance, which is faster on large inputs.

Insertion sort is actually very fast for sorting small arrays. Some standard libraries have sort functions that switch from a quicksort to insertion sort when the partition size is 10 or less.

I did a quick test comparing our `insertionSort()` with Swift's built-in `sort()`. On arrays of about 100 items or so, the difference in speed is tiny. However, as your input becomes larger, **O(n^2)** quickly starts to perform a lot worse than **O(n log n)** and insertion sort just can't keep up.

## See also

[Insertion sort on Wikipedia](https://en.wikipedia.org/wiki/Insertion_sort)

*Written for Swift Algorithm Club by Matthijs Hollemans*
