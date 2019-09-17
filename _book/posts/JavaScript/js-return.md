## JavaScript return 기능 정리

### return의 역할

1.함수의 실행을 종료하는 역할

```javascript
function counter(){
    for (var i = 1; i++){
        console.log(i);
        if (i == 5){
            return;
        }
    }
}
// 1 2 3 4 5
```



2.값을 리턴해주는 역할



### return문의 차이점

return : 조건이 참이면 해당 값을 호출한다.

return true : 조건이 참이면 true값을 호출한다.

return false : 조건이 참이면 false값을 호출하고 함수 실행을 종료한다.



```html
<form name="submitForm" action="submit.html">
    <input type="text" name="inpName">
    <button type="submit" name="submitBtn" onClick="javascript:return formCheck();">
        submit
    </button>
</form>
```



```javascript
function formCheck(){
    if(!document.submitForm.inpName.value){
        alert('내용을 입력해주세요');
        return false;
    }
}
```

이런 경우에 return false는 input안에 값이 없을 경우에 폼이 submit되는 상황을 방지해주는 역할을 한다.
