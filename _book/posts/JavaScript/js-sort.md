# [JavaScript] 함수 - sort()

> 배열의 요소를 정렬하여 반환하는 함수



#### 일반 사용

```javascript
Array.sort();
```

```javascript
var months = ['March', 'Jan', 'Feb', 'Dec'];

months.sort(); // ["Dec", "Feb", "Jan", "March"];


var numbers = [2, 30, 5, 100, 1];

numbers.sort(); // [1, 100, 2, 30, 5]
```



#### 숫자 정렬

```javascript
var numbers = [2, 30, 5, 100, 1];

// 오름차순
numbers.sort(function(a, b) {
    return a - b;
}); // [1, 2, 5, 30, 100]

// 내림차순
numbers.sort(function(a, b) {
    return b - a;
}); // [100, 30, 5, 2, 1]
```



#### 역순

```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort(); // 먼저 sort()로 순차정렬 후 
fruits.reverse(); // reverse()로 역순으로 변경
```





## Refer

[JavaScript Array Sort - W3Schools](<https://www.w3schools.com/js/js_array_sort.asp>)

[Array.prototype.sort() - JavaScript | MDN](<https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort>)