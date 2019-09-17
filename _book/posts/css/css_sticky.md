## position sticky 속성

- 일반적인 상태에서는`position: static;` 속성값과 동일하지만, 스크롤이 특정 위치까지 도달하는 경우 `position: fixed;` 속성처럼 화면에 고정시킬 수 있는 속성값.
- 사용하기 위해서는 `top`, `left`, `right`, `bottom` 등의 위치값을 필수로 정의해야 한다.
- ie에서는 호환이 되지 않는다.



```css
div {position: sticky; top: 20px;}
```

해당 경우에 div 태그는  화면상 상단으로부터 20px에 도달하기 전까지 다른 태그들처럼 배치되어 있다가, 임계점을 넘게 되면 상단으로부터 20px의 위치에 고정되게 된다.

