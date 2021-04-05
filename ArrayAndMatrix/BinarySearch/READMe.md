### 二分模版

------

【版本1-从右往左找】

当我们将区间 [l, r] 划分成[l, mid] 和 [mid + 1, r]时，其更新操作是r = mid或者 l = mid + 1, 计算mid时不需要+1。

```c++
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;
        else l = mid + 1;
    }
    return l;
}
```





【版本2-从左往右找】

当我们将区间 [l, r] 划分成[l, mid - 1] 和[mid, r]时，其更新操作是r = mid - 1 或者 l = mid，此时为了防止死循环，计算mid时需要加1。

```c++
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;
        else r = mid - 1;
    }
    return l;
}
```

