# [CSS] CSS 방법론

## css 방법론을 사용해야하는 이유
1. 쉬운 유지보수
2. 코드의 재사용 
3. 확장 가능
4. 직관적인 네이밍


## BEM
[BEM](http://getbem.com/ ) 은 블록(Block), 요소(Element), 수식어(Modifier) 를 네이밍의 주요 규칙으로 삼는 방법이다.

> 규칙
> - 클래스만 사용 가능하며 id, 태그는 사용하지 않는다.
> - 소문자와 숫자로만 작성한다.
> - 단어는 하이픈(-)으로 구분한다.

### 블록 (Block)
- 논리적, 혹은 기능적으로 독립 가능한 구성 요소
- 독립적인 블록은 개발 및 재사용을 용이하게 한다.
- 예시 ) header, logo, search, menu...

### 요소 (Element)
- 블록 안에서 특정 기능을 담당하는 부분
- 블록을 벗어나 외부적으로는 사용할 수 없음.
- block__element 형태로 사용 (더블 언더바)
- 요소는 없으면 생략 가능하다.
- 예시 ) header__title

### 수식어 (Modifier)
- 블록과 요소의 모양, 동작을 정의하는 역할.
- block__element--modifier , block--modifier 형태로 사용 (더블 하이픈)
- 수식어도 없으면 생략 가능하다.
- boolean 타입과 key-value 타입이 있다.
- boolead 타입 : true의 경우 수식어를 추가한다. (form__button--disabled)
- key-value 타입 : key-value의 형태로 수식어를 추가한다. (form__button--color-yellow)

## reference
http://getbem.com/introduction/
https://synerghetic.net/ awwwards winner인데 bem방식으로 작성되어있다. 
https://gomdoreepooh.github.io/notes/smacss-bem-oocss
https://medium.com/witinweb/css-%EB%B0%A9%EB%B2%95%EB%A1%A0-1-bem-block-element-modifier-1c03034e65a1
