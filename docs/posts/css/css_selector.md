## 태그 개수가 n개일 때 스타일 적용하기 



크기에서 유동적인 조정이 필요한 경우 대부분은 flex 속성을 쓰면 가능하지만, 가끔 flex속성이 없이 태그가 특정 개수일 때 스타일을 달리 적용해야 하는 상황이 있다. 

그럴 때 아래와 같이 선택자를 이용하여 별도의 javaScript 코드를 추가하지 않고 css만으로 제어할 수 있다.

```css
/* li가 한 개일 경우만 스타일 적용 */
li:first-child:nth-last-child(1) {
    width: 100%;
}
li:only-chile {
    width: 100%;
}
/* li가 두 개일 경우만 스타일 적용 */
li:first-child:nth-last-child(2),
li:first-child:nth-last-child(2) ~ li {
    width: 50%;
}
/* li가 세 개일 경우만 스타일 적용 */
li:first-child:nth-last-child(3),
li:first-child:nth-last-child(3) ~ li {
    width:33.3%;
}
```

