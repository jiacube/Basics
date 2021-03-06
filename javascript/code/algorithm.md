### 堆栈 队列

栈: 先进后出

队列: 先进先出

### 排序

#### 冒泡排序(Bubble Sort)

一种交换顺序，它的基本思想是: 两两比较相邻记录的关键字，如果反序则交换，直到没有反序的记录为止。

### 选择排序(Selection Sort)

通过n-i次关键字间的比较，从n-i+1个记录中选出关键字最小的记录，并和第i(1<=i<=n)个记录交换之。

### 插入排序(Insertion Sort)

将一个记录插入到已经排好序的有序表中，从而得到一个新的、记录数增1的有序表。

### 希尔排序(Shell Sort)

基本有序，就是小的关键字基本在前面，大的基本在后面，不大不小的基本在中间。

将相距某个"增量"的记录组成一个子序列，这样才能保证子序列内分别进行直接插入排序后得到的结果是基本有序而不是局部有序。

### 堆排序(Heap Sort)

堆是完全二叉树: 每个结点的值都大于或等于其左右孩子结点的值，称为大顶堆；或者每个结点的值都小于或等于其左右孩子结点的值，称为小顶堆。

### 归并排序(Merge Sort)

假设初始序列含有n个记录，则可以看成是n个有序的子序列，每个子序列的长度为1，然后两两归并，得到n/2个长度为2或1的有序子序列；再两两归并，...，如此重复，直至得到一个长度为n的有序序列为止，这种排序方法称为2路归并排序。

### 快速排序(Quick Sort)

通过一趟排序将待排记录分割成独立的两部分，其中一部分记录的关键字均比另一部分记录的关键字小，则可分别对这两部分记录继续进行排序，已达到整个序列有序的目的。
