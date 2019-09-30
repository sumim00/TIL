## Math 객체에서 자주 사용하는 메소드

##### Math.random();

0과 1사이의 난수를 반환.

```javascript
Math.random()		// 0.4399476925962085
```



##### Math.floor(x);

x의 내림한 수를 반환.

##### Math.ceil(x);

x의 올림한 수를 반환.

##### Math.round(x);

x의 반올림한 수를 반환.

```javascript
Math.floor(4.8)		// 4
Math.ceil(4.8)		// 5
Math.round(4.8)		// 5
```



##### Math.abs(x);

x의 절대값을 반환

```javascript
Math.abs(-123)		// 123
```



##### Math.max(x, y, z ...);

인수 중 가장 큰 수를 반환.

##### Math.min(x, y, z ...);

인수 중 가장 작은 수를 반환.

```javascript
Math.max(123,5,99) // 123
Math.min(123,5,99) // 5
```



##### Math.pow(x,y)

x의 y제곱을 반환.

##### Math.sqrt(x);

x의 제곱근을 반환.

```javascript
Math.pow(2,5)	// 32
Math.sqrt(49)	// 7
```





### Refer

[Math - JavaScript | MDN](<https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math>)