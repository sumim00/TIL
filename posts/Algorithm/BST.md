## Dynamic Set

- 여러 개의 키(key)를 저장

- 다음과 같은 연산들을 지원하는 자료구조

  - INSERT - 새로운 키의 삽입
  - SEARCH - 키 탐색
  - DELETE - 키의 삭제

- 예: 심볼 테이블

- 정렬된 혹은 정렬되지 않는 배열 혹은 연결 리스트를 사용할 경우,

  INSERT, SEARCH, DELETE 중 적어도 하나는 O(n)

- 방법 : 이진탐색트리, 레드-블랙 트리, AVL-트리 등



## 검색트리 (Search Tree)

- Dynamic set을 트리의 형태로 구현 (원래부터 트리의 구조를 가지지X)
- 일반적으로 INSERT, SEARCH, DELETE 연산이 트리의 높이(height)에 비례하는 시간복잡도를 가짐
- 이진검색트리, 레드-블랙 트리, B-트리 등



## 이진검색트리 (BST)

- 이진 트리이면서

- 각 노드에 하나의 키를 저장

- 각 노드 v에 대해서 그 노드의 왼쪽 부트리에 있는 키들은 key[v]보다 작거나 같고,

  오른쪽 부트리에 있는 값은 크거나 같다.

> heep과 유사하지만 heep은 complete binary tree만 가능하고 BST는 트리의 모양에 대해서는 제약이 없다. 
>
> 또한 heep은 부모 노드가 자식 노드보다 커야 한다는 Max Heap Property이 조건이지만, BST는 부모 노드는 왼쪽 부트리보다 작거나 같고 오른쪽 부트리보다 크거나 같아야 한다.



### SEARCH

> 루트 노드로 접근 -> 노드와 필요한 값을 대조하여 오른쪽 혹은 외쪽으로 이동

시간복잡도 : O(h), 여기서 h는 트리의 높이. 트리의 높이 h에 비례한다.

```bash
// recursion
TREE-SEARCH(x, k)
	if x = NIL or k = key[x]
		then return x
	if k < key[x]
		then return TREE-SEARCH(left[x], k)
		else return TREE-SEARCH(right[x], k)
		
// interative
INTERATIVE-TREE-SEARCH(x, k)
	while x ≠ NIL and k ≠ key[x]
		do if k < key[x]
			then x <- left[x]
			else x <- right[x]
	return x
```



#### 최소값, 최대값

- 최소값은 항상 가장 왼쪽 노드에 존재
- 최대값은 항상 가장 오른쪽 노드에 존재
- 시간복잡도: O(h)

```bash
TREE-MINIMUM(x)
	while left[x] ≠ NIL
		do x <- left[x]
	return x
	
TREE-MAXIMUM(x)
	while right[x] ≠ NIL
		do x <- right[x]
	return x
```



#### Successor

- 노드 x의 successor란 key[x]보다 크면서 가장 작은 키를 가진 노드
- 모든 키들이 서로 다르다고 가정 
- 3가지 경우
  - 노드 x의 오른쪽 부트리가 존재할 경우, 오른쪽 부트리의 최소값.
  - 오른쪽 부트리가 없는 경우, 부모를 따라 루트까지 올라가면서 처음으로 누군가의 왼쪽 자식이 되는 노드
  - 그런 노드가 존재하지 않을 경우 successor가 존재하지 않음. (즉, x가 최대값)
- 시간복잡도: O(h)

```bash
TREE-SUCCESSOR(x)
	if right[x] ≠ NIL
		then return TREE-MINIMUM(right[x])
	y <- [x]
	while y ≠ NIL and x = right[y]
		do x <- y
			y <- p[y]
	return y
```



#### Predecessor

- 노드 x의 predecessor란 key[x]보다 작으면서 가장 큰 키를 가진 노드
- Successor와 반대





### INSERT

- 기존의 노드를 변환하지 않고 추가
- x, y 2개의 트리를 사용
- 시간복잡도: O(h)

```bash
TREE-INSERT(T,z)
	y <- NIL
	x <- root[T]
	while x ≠ NIL
		do y <- x
			if key[z] < key[x]
				then x <- left[x]
				else x <- right[x]
	p[z] <- y
	if y = NIL
		then root[T] <- z	// 빈 트리인 경우
		else if key[z] < key[y]
			then left[y] <- z
			else right[y] <- z
```



### DELETE

- SEARCH 연산 이후 노드를 삭제
- 3가지 경우
  - Case 1: 자식 노드가 없는 경우, 그냥 삭제
  - Case 2: 자식 노드가 1개인 경우, 자신의 자식노드를 원래 자신의 위치로  (선형적이기 때문에 A-B-C 를 A-C로 바꾼다고 생각)
  - Case 3: 자식노드가 2개인 경우, successor 또는 predecessor의 값을 삭제하려는 노드로 copy한 뒤 successor 노드를 대신 삭제한다.
- 시간복잡도: O(h)

```bash
TREE-DELETE(T, z)
	if left[z] = NIL or right[z] = NIL
		then y <- z
		else y <- TREE-SUCCESSOR(z)
	if left[y] ≠ NIL
		then x <- left[y]
		else x <- right[y]
	if x ≠ NIL
		then p[x] <- p[y]
	if p[y] = NIL
		then root[T] <- x
        else if y = left[p[y]]
        	then left[p[y]] <- x
        	else right[p[y]] <- x
   	if y ≠ z
   		then key[z] <- key[y]
   			copy y's satellite data into z
   	return y
```



## BST 결론

- 각종 연산의 시간복잡도는 O(h)
- 그러나, 최악의 경우 트리의 높이 h=O(n)
- 균형잡힌 트리
  - 레드-블랙 트리 등
  - 키의 삽입이나 삭제시 추가로 트리의 균형을 잡아줌으로써 높이를 O(log₂n)으로 유지



## Refer

[인프런 - 영리한 프로그래밍을 위한 알고리즘 강좌]([https://www.inflearn.com/course/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%95%EC%A2%8C/lecture/4097](https://www.inflearn.com/course/알고리즘-강좌/lecture/4097))