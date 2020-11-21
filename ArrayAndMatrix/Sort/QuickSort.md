#### QuickSort

------

【难度】 ⭐ ⭐

【题目】

实现快速排序

1.  快速排序传入参数分别为需要排序的数组 nums，数组需要排序的开始索引low和结尾索引high
2.  递归终止条件：low >= hight,则完成排序，不用返回任何值。
3.  进入partition函数，取最高位的元素计作pivot，最低位的索引减去1计作i，用与确定pivot最后所处的索引位置
4.  从low到high遍历元素，如果值比pivot值小，则i+=1，索引 i 和 j 上面的元素交换位置。遍历结束确定pivot的位置为i+1，并且交换high位和i+1位的元素。
5.  递归调用quicksort 区间 low->pi -1 和 pi + 1 -> high。

```python
class Solution:
    def quickSort(self, nums:List[int], low:int, high:int):
        if low < high:
            pi = self.partition(nums, low, high)
            
            self.quickSort(nums, low , pi - 1)
            self.quickSort(nums, pi + 1, high)
    def partition(self, nums:List[int], low:int, high: int) -> int:
        pivot = nums[high]
        i = low - 1
        for j in range(low, high):
            if num[j] <= pivot:
                i += 1
            	nums[i], nums[j] = nums[j], nums[i]
        nums[high], nums[i+1] = nums[i+i], nums[high]
        return i + 1
        
```



```c++
#include <iostream>

using namespace std;

const int N = 100010;
int q[N];
void quickSort(int q[], int l, int r){
    if (l >= r) return;
    int x = q[(r + l) >> 1], i = l - 1, j = r + 1;
    while(i < j){
        do i ++; while(q[i] < x);
        do j --; while(q[i] > x);
        if (i < j) swap(q[i], q[j]);
    }
    quickSort(q, l, j);
    quickSort(q, j + 1, r);
}
int main(){
    int n;
    scanf("%d", n);
    for (int i = 0; i < n; i ++) scanf("%d", q[i]);
    quickSort(q, 0, n - 1);
    for (int i = 0; i < n; i ++) printf("%d ", q[i]);
    return 0;
}
```

