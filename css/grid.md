#  CSS grid 레이아웃

### 정리

그리드의 공간, 길이, 퍼센트나 비율을 정할 수 있다.

| 부모 요소 속성        | 설명            | 자식 요소 속성    | 설명           |
| --------------------- | --------------- | ----------------- | -------------- |
| display               | 정의            | grid-column-start | 행 시작 트랙   |
| grid-template-columns | 열 개수 및 크기 | grid-column-end   | 행 마지막 트랙 |
| grid-template-rows    | 행 개수 및 크기 | grid-row-start    | 열 시작 트랙   |
| grid-template-areas   | 개별 선언       | grid-row-end      | 열 마지막 트랙 |
| grid-auto-columns     | 자동 행맞춤     | grid-area         | 위의 4개 통합  |
| grid-auto-rows        | 자동 열맞춤     |                   |                |
| grid-gap              | 트랙 사이 간격  |                   |                |
|                       |                 |                   |                |

예시

```css
.wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 50px 50px
}
```

이렇게 부모 요소를 저장하게 되면 가로 3개 세로 2개씩 자식 요소들이 만들어지고, 가로 길이는 부모의 1/3 , 세로 길이는 50px로 정해진다.



