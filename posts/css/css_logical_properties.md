# [CSS] 논리적 속성 (CSS Logical Properties)

### 왜 논리적 속성이 중요할까

대부분의 개발자들은 CSS 위치를 지정할 때 `top`과 `bottom`, `left`와 `right`를 사용하곤 한다. 그러나 단순히 데이터를 송수신했던 이전의 웹과는 현대의 웹은 다양한 언어의 사람들이 소통하는 장이 되었고, 그만큼 개발에서도 그 다양성을 수용해야하는 시기이다.

이런 면에서 현재의 물리적 방향 설정 방법은 언어의 다양성을 고려하며 작업하기엔 힘든 상황이다. 아랍권에선 right to left 방식을 사용하고 있으며, 일본의 경우는 위에서 아래로 문자열이 진행된다. 

그런 맥락에서 CSS 논리적 속성은 기존의 물리적 방향 선언이 아닌 논리적인 속성 및 값을 설정함으로써 유연한 레이아웃 제어를 가능하게 한다.



### 기존 속성과 비교

박스 모델을 생각할 때, 우리는 일반적으로 아래와 같은 이미지를 떠올린다. x축과 y축이 절대적으로 정해져 있으며, 우리는 이를 기준으로 위아래, 좌우를 정의한다.

![물리적 속성](https://cdn-images-1.medium.com/max/1000/1*1EXpE-VzrUbV69aeWf1IGA.png)



그러나 논리적 속성에서는, 기존의 `top`, `bottom`, `left`, `right` 로 사고하는 형태에서 벗어나, 이를 `inline-start`, `inline-end`, `block-start`, `block-end` 로 대체한다.



![논리적 속성](https://cdn-images-1.medium.com/max/1000/1*KD9Qh9eo04XLnbHu1_UOcg.png)



### 논리적 속성, 속성값 정리

영어(LTR) 기준



#### Sizing 속성

`width` **=** `inline-size`

`height` **=** `block-size`



#### Margin, Border, Padding 속성

##### margin

`margin-block-start` = `margin-top`
`margin-block-end` = `margin-bottom`
`margin-inline-start` = `margin-left`
`margin-inline-end` = `margin-right`



##### padding

`padding-block-start` = `padding-top`
`padding-block-end` = `padding-bottom`
`padding-inline-start` = `padding-left`
`padding-inline-end` = `padding-right`



##### border

`border-block-start `= `border-top`
`border-block-end` = `border-bottom`
`border-inline-start` = `border-left`
`border-inline-end` = `border-right`



#### Float, Position 속성

##### position

`top` = `inset-block-start`
`bottom` = `inset-block-end`
`left` = `inset-inline-start`
`right` = `inset-inline-end`



##### float

`float: left` = `float: inline-start`
`float: right` = `float: inline-end`



#### 기타

`text-align :left` = `text-align: start;`
`text-align :right` = `text-align: end;`



## Refer

[CSS Logical Properties and Values - CSS: Cascading Style Sheets | MDN](<https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties>)

[New CSS Logical Properties! – Elad Shechter – Medium](<https://medium.com/@elad/new-css-logical-properties-bc6945311ce7>)

[How to Use CSS Logical Properties to Control Layout](<https://webdesign.tutsplus.com/tutorials/how-to-use-css-logical-properties--cms-33024>)