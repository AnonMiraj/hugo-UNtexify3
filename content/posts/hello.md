+++
title = 'Hello'
date = 2023-11-16T23:04:56Z
+++
- insertion is work by incremental method 

>[!NOTE]
> 1- there is another method that call divide and concer the worth case in it less than the insertion sort 
> 2- the second advantage is the the analizing its runing time is easy 


#  The divide-and-conquer method

```md
they break the problem into several
subproblems that are similar to the original problem but smaller in size
and combine it in one sorted array 
```

_**the base case—you just solve it directly without recursing**_

## the recursive case—you perform three characteristic steps
>1- Divide the problem into one or more subproblems that are smaller
>instances of the same problem
>2- Conquer the subproblems by solving them recursively.
>3- Combine the subproblem solutions to form a solution to the original problem.


- merge sort use this method 
  by the same 3 steps you can saw it in the book 
```cpp

#include <algorithm>
#include <bitset>
#include <cmath>
#include <iomanip>
#include <iostream>
#include <map>
#include <queue>
#include <set>
#include <stack>
#include <string>
#include <utility>
#include <vector>
// 48-57 -> 0-9  65-90 -> A-Z 97-122 -> a-z
#define fastio()                                                               \
  ios_base::sync_with_stdio(false);                                            \
  cin.tie(NULL);                                                               
#define ll long long
#define endl "\n"
using namespace std;


void merge(int arr[], int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;

    int L[n1], R[n2];
    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];

    int i = 0, j = 0, k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }

    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;

        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);

        merge(arr, l, m, r);
    }
}
void print(int *arr,int size)
{
  for(int i=0;i<size;i++)
    cout<<arr[i]<<" ";
  cout<<endl;
}

int main() {

  //  freopen("whereami.in", "r", stdin);
  //  freopen("whereami.out", "w", stdout);
  fastio();
  
  int size;
  int arr[] = { 12, 11, 13, 5, 6, 7 };

  size = sizeof(arr)/sizeof(arr[0]);

  print(arr,size);

  mergeSort(arr,0,11);

  print(arr,size);

  return 0;
}

```

