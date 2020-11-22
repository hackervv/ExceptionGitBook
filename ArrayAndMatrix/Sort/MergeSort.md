#### MergeSort

------

【难度】 ⭐ ⭐

【题目】

实现归并排序

1.  函数传入参数需要排序的数组 nums，数组左边界 left，右边界 right。
2.  递归终止条件为left >= right，取left与right的中间点mid，分别对left到mid和mid+1到right区间递归调用函数。
3.  进入merge函数，i，j分别计作参数left和mid，比较num[i]和nums[j]的大小，小的加入到临时数组中，并且较小的+=1。
4.  循环执行步骤3中的比较操作，直到i > mid 或者 j > right 时跳出循环。如果i <=mid，则将i到mid的元素加入到tmp中，如果j <= right，则将j到right的元素加入到tmp中。
5.  将临时数组tmp替换到到nums中。

```python
class Solution:
    def mergeSort(self, nums:List[int], left:int, right:int):
        if left < right:
            mid = (left + right) >> 1
            
            self.mergeSort(nums, left, mid)
            self.mergeSort(nums, mid + 1, right)
            
            self.merge(nums, left, mid, right)
            
    def merge(self, nums:List[int], left:int, mid:int, right:int):
        tmp = []
        i, j = left, mid+1
        while i <= mid and j <= right:
            if nums[i] <= nums[j]:
                tmp.append(nums[i])
                i += 1
            else:
                tmp.append(nums[j])
                j += 1
        if i <= mid:
            tmp.extend(nums[i:mid+1])
        if j <= right:
            tmp.extend(nums[j:right+1])
        for p in tmp:
            nums[left] = p
            left += 1
        
```





```c++
#include <iostream>

using namespace std;

const int N;
int q[N];
int tmp[N];

void mergeSort(int q[], int l, int r){
    if (l >= r) return;
    int mid = (r + l) >> 1;
    mergeSort(q, l, mid), mergeSort(mid + 1, r);
    int k = 0, i = l, j = mid + 1;
    while (i < j)
        if (q[i] <= q[j]) tmp[k ++] = q[i ++];
    	else tmp[k ++] = q[j ++];
    while (i <= mid) tmp[k ++] = q[i ++];
    while (j <= r) tmp[k ++] = q[i ++];
    for (int i = l, j = 0; i <= r; i ++,j ++) q[i] = tmp[j];
    
}

int main(){
    int n;
    scanf("%d", &n);
    for (int i = 0; i < n; i ++) scanf("%d", q[i]);
    mergeSort(q, 0, n-1);
    for (int i = 0; i < n; i ++) printf("%d ", q[i]);
    return 0;
}
```

