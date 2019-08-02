[toc]
## 1. 二分查找算法
### 算法描述
- 二分查找算法要求线性表必须采用顺序存储结构，而且表中元素按关键字有序排列。
- 对于给定的值，如果数组元素中存在该值，则返回其下标，不存在则返回-1。
- 两种解法：循环实现和递归实现。

### 实现一、循环实现二分查找
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

### 实现二、递归实现二分查找
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

## 2. 反转单链表
### 算法描述
     反转单链表，示例如下:
     <pre>
          输入: 1->2->3->4->5->NULL
          输出: 5->4->3->2->1->NULL
     </pre>
     
### 实现一、依次删除head后节点并插入到链表头部的实现
```java
 /**
     * 节点前插实现：每次将head后面的节点删除，然后插入到头部，直到head后面没有节点为止
     * @param head
     * @return
     */
    public static ListNode reverseList(ListNode head) {
        if (head == null) {
            return null;
        }
        ListNode newHead = head;
        while (head.next != null){
            ListNode tmpNode = newHead;
            newHead = head.next;
            head.next = head.next.next;
            newHead.next = tmpNode;
        }
        return newHead;
    }
```

### 实现二、保留当前节点的前、后节点，修改next指向的实现
```java
/**
     * 依次遍历单链表修改next指向实现：在修改当前curr节点时，需预先保留好pre、next节点，依次遍历。
     * @param head
     * @return
     */
    public static ListNode reverseList(ListNode head) {
        ListNode pre = null;
        ListNode curr = head;
        while (curr!=null){
            ListNode nextTmp = curr.next;
            curr.next=pre;
            pre=curr;
            curr=nextTmp;
        }
        return pre;
    }
```

## 3. 斐波那契数列求第n项
### 算法描述
     斐波那契数，通常用 F(n) 表示，形成的序列称为斐波那契数列。该数列由 0 和 1 开始，后面的每一项数字都是前面两项数字的和。也就是：
     <pre>
          F(0) = 0,   F(1) = 1
          F(n) = F(n - 1) + F(n - 2), 其中 n > 1.
     </pre>
     给定 n，计算 F(n)。
     
### 实现一、递归实现
```java
     /**
     * 斐波那契数列求第n项-递归实现
     * @param n
     * @return
     */
    public int fibnaci(int n) {
        if (n == 1) {
            return 0;
        } else if (n == 2) {
            return 1;
        } else {
            return fibnaci(n-1) + fibnaci(n-2);
        }
    }
```
