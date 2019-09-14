## JavaScript 모바일 OS 체크하기



#### match 메서드를 이용한 OS 체크

```javascript
var android = navigator.userAgent.match(/android/gi) != null,
    ios = navigator.userAgent.match(/iphone|ipad|ipod/gi) != null;

// match 메서드를 이용해 해당 정규식과 일치하는지 여부를 판단하고 boolean타입 값을 가져온다.

if(android){
    
} else if(ios) {
    
}
// 얻어온 boolean 타입 변수를 가지고 if문을 사용해 제어한다.
```



#### indexOf 메서드를 이용한 OS 체크

```javascript
var android = navigator.userAgent.toLowerCase().indexOf('android') > -1,
	iphone = navigator.userAgent.toLowerCase().indexOf('iphone') > -1;

// 사용중인 디바이스가 indexOf의 값과 일치할 경우 true값을, 아니라면 false값을 가진다.
	
if(android){
    
} else if (iphone){
    
};
// 얻어온 boolean 타입 변수를 가지고 if문을 사용해 제어한다.
```



navigator : 브라우저의 정보를 제공하는 객체

userAgent : uset-agent 헤더를 반환하는 프로퍼티
