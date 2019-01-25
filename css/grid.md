#  CSS grid 레이아웃

grid는 2017년에 새로 만들어진 레이아웃이다. 기존 flex와는 달리 2차원적인 배치까지 가능하다는 것이 장점인데, 벤더 프리픽스와 대체 코드를 삽입함으로써 크로스 브라우징이 가능하고, flex와 마찬가지로 유연한 레이아웃 설정이 가능하기 때문에 반응형 페이지 작업 또한 적합하다.



### 속성 정리

| 부모 요소 속성             | 설명               | 자식 요소 속성        | 설명           |
| -------------------------- | ------------------ | --------------------- | -------------- |
| display                    | 정의               | grid-column-start/end | 행 시작 트랙   |
| grid-template-columns/rows | 열/행 개수 및 크기 | grid-row-start/end    | 행 마지막 트랙 |
| grid-template-areas        | 개별 선언          | grid-area             | 위의 4개 통합  |
| grid-gap                   | 자동 행/열 맞춤    |                       |                |
|                            |                    |                       |                |



### 키워드 정리

| 키워드명      | 설명                                                         |
| ------------- | ------------------------------------------------------------ |
| fr (fraction) | 값을 동일하게 나누기 위한 일종의 변수 (1200 = 4x의 x같은 개념) |
| span          | 현재 기준점                                                  |
| repeat(x / y) | y값을 x번 반복                                               |
|               |                                                              |



### 주의

자식 요소 중 display:inline-block , display:table-cell , vertical-align , column-* 속성은 그리드 속성이 적용되지 않는다.



### 작업 파일

https://jsfiddle.net/sumim/pv0daLtx/41/



### Reference

https://alligator.io/css/css-grid-layout-fr-unit/

https://www.vobour.com/-%EB%94%94%EC%9E%90%EC%9D%B8-%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EC%9D%84-%EA%B5%AC%EC%84%B1%ED%95%A0%EB%95%8C-css-grid%EA%B0%80-bootstrap%EB%B3%B4%EB%8B%A4-%EB%82%98

https://www.w3schools.com/css/css_grid_item.asp
