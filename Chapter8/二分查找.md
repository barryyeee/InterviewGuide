# 二分查找

```java
public int find(int[] arr, int target) {
    int left = 0, right = arr.length;
    while(left < right) {
        int mid = left + (right - left) / 2;
        if(arr[mid] < target) {
            left = mid + 1;
        }
        else {
            right = mid;
        }
    }
    /*查找第一个不小于target的数*/
    return right == arr.length ? -1 : arr[right];
    /*查找最后一个小于target的数*/
    //return right == arr.length ? -1 : arr[right - 1];
}
```

```java
public int find(int[] arr, int target) {
    int left = 0, right = arr.length;
    while(left < right) {
        int mid = left + (right - left) / 2;
        if(arr[mid] <= target) {
            left = mid + 1;
        }
        else {
            right = mid;
        }
    }
    /*查找第一个大于target的数*/
    return right == arr.length ? -1 : arr[right];
    /*查找最后一个不大于target的数*/
    //return right == arr.length ? -1 : arr[right - 1];
}
```