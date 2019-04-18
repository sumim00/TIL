## CSS animation, keyframe 속성

애니메이션 속성은 CSS3 속성 중 하나이며, 원하는 시간에 원하는 CSS스타일을 정의하는 기능을 갖고 있다. 사용 방법은 @keyframe으로 고유한 애니메이션을 생성하고 animation 속성을 이용해 원하는 태그에 해당 애니메이션을 적용한다.



#### 키프레임 정의 예시

```css
@keyframes move {
    from {margin-left: 0;}
    to {margin-left: 100px;}
}

@keyframes gradation {
    0% {background-color: red;}
    20% {background-color: orange;}
    40% {background-color: yellow;}
    60% {background-color: green;}
    80% {background-color: blue;}
    100% {background-color: purple;}
}
```



#### 애니메이션 속성 적용 예시

```css
div {
    animation-name: move; /*이름*/
    animation-duration: 3s; /*재생 시간*/
    animation-timing-function: linear | ease | ease-in | ease-out | ease-in-out;
     /*앞뒤 속도*/
    animation-delay: 2s; /*지연 시간*/
    animation-interaction-count: 3; /*반복 횟수*/
    animation-direction: alternate; /*재생 중이 아닐 때*/
}

div {
    animation: move 3s ease-in 2s 3 alternate; /*축약형*/
}
```

