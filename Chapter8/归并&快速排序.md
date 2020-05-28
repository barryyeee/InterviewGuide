# 归并&快速排序

```java
//归并排序
public void mergeSort(int[] arr, int left, int right) {
    if(left >= right) return;
    int mid = left + (right - left) / 2;
    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);
    partition(arr, left, right, mid);
}
public void partition(int[] arr, int left, int right, int mid) {
    int[] res = new int[right - left + 1];
    int i = left, j = mid + 1, index = 0;
    while(i <= mid && j <= right) {
        if(arr[i] < arr[j]) {
            res[index++] = arr[i++];
        }
        else {
            res[index++] = arr[j++];
        }
    }
    while(i <= mid) {
        res[index++] = arr[i++];
    }
    while(j <= right) {
        res[index++] = arr[j++];
    }
    for(int num : res) {
        arr[left++] = num;
    }
}
```

```java
//快速排序
public void quickSort(int[] arr, int begin, int end) {
    if(begin >= end) return;
    int base = arr[begin];
    int i = begin, j = end;
    while(i < j) {
        while(i < j && arr[j] >= base) {
            j--;
        }
        while(i < j && arr[i] <= base) {
            i++;
        }
        if(i < j) {
            int tmp = arr[i];
            arr[i] = arr[j];
            arr[j] = tmp;
        }
    }
    arr[begin] = arr[j];
    arr[j] = base;
    quickSort(arr, begin, j - 1);
    quickSort(arr, j + 1, end);
}
```

