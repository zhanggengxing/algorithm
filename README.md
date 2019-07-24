[toc]
## 1. 二分查找算法
### 算法描述
- 二分查找算法要求线性表必须采用顺序存储结构，而且表中元素按关键字有序排列。
- 对于给定的值，如果数组元素中存在该值，则返回其下标，不存在则返回-1。
- 两种解法：循环实现和递归实现。
### 循环实现二分查找
```java
     /*
     * 循环实现二分查找
     */
    public static int binarySearch(int[] arr, int data) {
        int low = 0;
        int high = arr.length - 1;
        while (low <= high) {
            //如果low，high比较大,low+high有可能溢出
            int middle = low + (high-low) / 2;
            if (data == arr[middle]) {
                return middle;
            } else if (data < arr[middle]) {
                high = middle - 1;
            } else {
                low = middle + 1;
            }
        }
        return -1;
    }
```
### 递归实现二分查找
```java
     /**
     * 递归实现二分查找
     */
    public static int binarySearch(int[] num, int data, int low, int high) {

        if (data < num[low] || data > num[high] || low > high) {
            return -1;
        }
        //如果low，high比较大,low+high有可能溢出
        int midIndex = low + (high - low) / 2;

        if (data < num[midIndex]) {
            return binarySearch(num, data, low, midIndex - 1);
        } else if (data > num[midIndex]) {
            return binarySearch(num, data, midIndex + 1, high);
        } else {
            return midIndex;
        }
    }
```
