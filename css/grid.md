###  CSS grid 속성

부모 요소

그리드의 공간, 길이, 퍼센트나 비율을 정할 수 있다.

| grid-template-columns | grid-template-rows   |
| --------------------- | -------------------- |
| 행 갯수 및 크기 설정  | 열 갯수 및 크기 설정 |

예시

```css
.wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 50px 50px
}
```

이렇게 부모 요소를 저장하게 되면 가로 3개 세로 2개씩 자식 요소들이 만들어지고, 가로 길이는 부모의 1/3 , 세로 길이는 50px로 정해진다.



