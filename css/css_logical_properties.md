## CSS 논리적 속성 (CSS Logical Properties)

### 왜 논리적 속성이 중요할까

대부분의 개발자들은 CSS 위치를 지정할 때 `top`과 `bottom`, `left`와 `right`를 사용하곤 한다. 그러나 단순히 데이터를 송수신했던 이전의 웹과는 현대의 웹은 다양한 언어의 사람들이 소통하는 장이 되었고, 그만큼 개발에서도 그 다양성을 수용해야하는 시기이다.

이런 면에서 현재의 물리적 방향 설정 방법은 언어의 다양성을 고려하며 작업하기엔 힘든 상황이다. 아랍권에선 right to left 방식을 사용하고 있으며, 일본의 경우는 위에서 아래로 문자열이 진행된다. 

그런 맥락에서 CSS 논리적 속성은 기존의 물리적 방향 선언이 아닌 논리적인 속성 및 값을 설정함으로써 유연한 레이아웃 제어를 가능하게 한다.



### 변경되는 속성 (라틴문화권 기준)

| 물리적 속성 | 논리적 속성  |
| ----------- | ------------ |
| width       | inline-size  |
| height      | block-size   |
| left        | inline-start |
| right       | inline-end   |
| top         | block-start  |
| bottom      | block-end    |





## Refer

[CSS Logical Properties and Values - CSS: Cascading Style Sheets | MDN](<https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties>)

[New CSS Logical Properties! – Elad Shechter – Medium](<https://medium.com/@elad/new-css-logical-properties-bc6945311ce7>)

[How to Use CSS Logical Properties to Control Layout](<https://webdesign.tutsplus.com/tutorials/how-to-use-css-logical-properties--cms-33024>)