#### 정렬 (Updated)

##### 종류

- Bubble sort
- Insertion sort
- Selection sort (가장 큰 값을 마지막에 놓고, 남은 값 중 가장 큰 값을 찾는 정렬)
- Quicksort
- Merge sort
- Heap sort
- Redix sort

#### Selection Sort

1. A[1...last] 중 가장 큰 수 A[k]를 찾는다.
2. A[k]와 A[last]의 값을 교환

시간복잡도 

for 루프는 n-1번 반복

실행시간: T(n) = (n-1)+(n-2)+ ... +2+1 = Θ(n²)

최악, 최선, 평균 시간복잡도가 동일하다.



#### Bubble Sort

1. 자기 자신과 그 다음 숫자와 비교한다.
2. 본인이 더 클 경우 값을 교환

실행시간: T(n) = (n-1)+(n-2)+ ... +2+1 = O(n²)

최악, 최선, 평균 시간복잡도가 동일하다.



#### 삽입정렬 Insertion Sort

1. for 루프는 n-1번 반복
2. A[1...n]의 적당한 자리에 A[i]를 삽입한다.

최악의 경우: T(n) = (n-1)+(n-2)+ ... +2+1 = O(n²)



#### 합병정렬 Merge Sort

분할정복법이란

분할 -> 정복 -> 합병의 순으로 답을 구하는 방법

분할: 해결하고자 하는 문제를 작은 크기의 동일한 문제들로 분할

정복: 각각의 작은 문제를 순환적으로 해결

합병: 작은 문제의 해를 합하여(merge) 원래 문제에 대한 해를 구함.

본질적으로 reqursion을 이용하여 문제를 찾는다.



1. 데이터가 저장된 배열을 절반으로 나눔 (devide)
2. 각각을 순환적으로 정렬 (recursively sort)
3. 정렬된 두 개의 배열을 합쳐 전체를 정렬 (merge / 이 과정이 실질적으로 정렬이 진행되는 부분)

```java
mergeSort(A[], p, r)
{
    if (p < r) then {
        q = (p+r)/2; //중간 지점 계산
        mergeSort(A, p, q) //전반부 정렬
        mergeSort(A, q+1, r) //후반부 정렬
        merge(A, p, q, r); //합병
    }
}
merge(A[], p, q, r)
{
    정렬되어 있는 두 배열 A[p...q]와 A[q+1...r]을 합하여
    정렬된 하나의 배열 A[p...r]을 만든다.
}

void merge ( int data[], int p, int q, int r ){
    int i=p, j=q+1, k=p;
    int tmp[data.length()];
    while (i<=q && j<=r) {
        if (data[i] <= data[j])
            tmp[k++]=data[i++];
        else
            tmp[k++]=data[j++];
    }
    while (i<=q)
        tmp[k++]=data[i++];
    while (j<=r)
        tmp[k++]=data[j++];
    for (int i=p; i<=r; i++)
        data[i]=tmp[i];
}
```

시간복잡도 : T(n) = 2T(n/2) + n (절반의 시간복잡도를 구하고, 마지막으로 merge하는 과정이 n번 반복) = == O(n log n)

if n = 1, T(n) = 0



#### 빠른정렬 (Quicksort)

데이터를 분할하는 방법이 merge sort와 다르다.

merge sort는 1/2 1/2로 분할하는 반면 피봇을 기준으로 분할하기 때문에 정확한 반을

분할할 수 없다.

분할: 배열을 pivot을 기준으로 작은 값과 큰 값으로 나눈다.(partition)

정복: 각 부분은 순환적(reqursion)으로 정렬한다.

합병: nothing to do

최악의 시간복잡도 : T(n) = Θ (n²)

최선의 시간복잡도 : T(n) = Θ (n log n) (항상 절반으로 분할되는 경우)

balanced : T(n) = Θ (n log n) -> 분할이 아주 극단적으로 이루어지지 않으면 빠르다.

항상 일정하지 않으므로 최악의 경우를 생각 (최악 : 이미 정렬된 경우, 피봇보다 큰 애가 없는 경우)



pivot의 선택

1. 첫번째 값이나 마지막 값을 피봇으로 선택 (x)현실의 데이터는 랜덤하지 않기 때
2. 중간값을 선택 (최악의 경우 시간복잡도가 달라지지는 않음)
3. 랜덤하게 선택 (평균 시간복잡도)



#### Heap과 Heapsort

- 최악의 시간복잡도 : T(n) = Θ (n log n) 
- Sorts in place - 추가 배열 불필요
- 이진 힙(binary heap) 자료구조를 사용

##### Heap의 정의

- complete binary tree(마지막 레벨에는 가장 오른쪽부터 연속된 몇 개의 노드가 비어있을 수 있음)
- heap property를 만족
  - max heap property (부모는 자식보다 크거나 같다)
  - min heap property (부모는 자식보다 작거나 같다)

##### Max-Heapify

- 트리의 전체 모양은 complete binary tree이며
- 왼쪽 부트리와, 오른쪽 부트리도 그 자체로 heap이며
- 유일하게 루트만이 heap property를 만족하지 않을 때
- 전체를 힙으로 만드는 기본 연산!

시간복잡도 : T(n) = log n

두 자식들 중 더 큰 쪽이 나보다 크면 exchange한다.

1. 정렬할 배열을 힙으로 만든다.
2. heapify를 이용하여 연산한다.

시간복잡도 : T(n) = O(n)

```
// recursive version
MAX-HEAPIFY(A, i)
{
	if there is no child of A[i]
	 return;
	k <- index of the biggest child of i;
	if A[i] >= A[k]
        return;
    exchange A[i] and A[k];
    MAX-HEAPIFY(A, k);
}

// interactive version
MAX-HEAPIFY(A, i)
{
	while A[i] has a child do
		k <- index of the biggest child of i;
		if A[i] >= A[k]
			return;
		exchange A[i] and A[k];
		i = k;
	end.
}
```



#### Heapsort

1. 주어진 데이터로 힙을 만든다.
2. 힙에서 최대값(루트)을 가장 마지막 값과 바꾼다.
3. 힙의 크기가 1 줄어든 것으로 간주한다. 즉, 가장 마지막 값은 힙의 일부가 아닌 것으로 간주한다.
4. 루트노드에 대하여 Heapify(1)한다
5. 2~4번을 반복한다.

시간복잡도 : T(n) = O(n log₂ n)

```
HEAPSORT(A)
1. BUILD-MAX-HEAP(A)	: O(n)
2. for i <- heap_size downto 2 do	: n-1 times
3. 	exchange A[1] <-> A[i] 			: O(1)
4. 	heap_size <- heap_size -1 		: O(1)
5. 	MAX-HEAPIFY(A, 1)				: O(n log₂ n)
```



