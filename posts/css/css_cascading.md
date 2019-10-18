# [CSS] 스타일 상속과 우선 순위

CSS가 Cascading Style Sheet의 약자인 만큼 Cascading은 CSS를 정의하는 대표적인 키워드이다.



#### 상속과 Cascading

상속이란 상위(부모, 조상) 요소에 적용된 프로퍼티를 하위(자식, 자손) 요소가 물려받는 특성을 의미한다.



#### Cascading

요소는 하나 이상의 CSS 선언에 영향을 받을 수 있다. 이 때 충돌을 피하기 위해서 CSS 적용 우선순위가 필요한데, 이를 캐스캐이딩(Cascading)이라고 한다.

캐스캐이딩은 다음과 같은 3가지 규칙에 따라 적용한다.

1. 중요도 : 어디에 선언되었는가
2. 명시도 : 대상을 명확하게 특정했는가
3. 선언순서 : 어느 위치에 선언되었는가



#### 중요도

1에서 5로 내려갈수록 중요도가 커진다.

1. head 요소 내의 style 요소
2. head 요소 내의 style 요소 내의 `@import` 문
3. `<link>` 로 연결된 CSS 파일
4. `<link>` 로 연결된 CSS 파일 내의 `@import` 문
5. 브라우저 디폴트 스타일시트



#### 명시도

1에서 7로 내려갈수록 명시도가 커진다.

1. `!important` 
2. 인라인 스타일 
3. 아이디 선택자 
4. 클래스/어트리뷰트/가상 선택자 
5. 태그 선택자 
6. 전체 선택자 
7. 상위 요소에 의해 상속된 속성



#### 선언순서 

나중에 선언된 스타일이 우선 적용된다.

```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            p { color: blue; }
            p { color: red; }
        </style>
    </head>
    <body>
      <p>What is my Color ?</p><!-- 글자색은 red로 적용된다 -->
    </body>
</html>
```





#### 참고 사이트

우선순위에 따라 점수를 매겨주는 사이트이다.

<https://specificity.keegan.st/>





## Refer

[](<https://poiemaweb.com/css3-inheritance-cascading>)