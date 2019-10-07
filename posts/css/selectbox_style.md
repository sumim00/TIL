# [CSS] selectbox 스타일 변경

오늘은 selectbox 스타일을 변경하는 방법에 대해 배웠다. selectbox는 PC 브라우저 / ios / 안드로이드 와 같이  사용자 환경에 따라 각기 다른 스타일이 적용된다. 따라서 프로젝트에 따라 selectbox 스타일을 통일시켜야 하는 경우가 생기는데, 이럴 때 다음과 같은 방법을 사용한다.

** 다만 ie9이하부터는 적용되지 않으므로, 하위 버전까지 적용하기 위해서는 추가적인 js코드가 필요하다. 



#### [공통] html

```html
<span class="select_custom select_type1">
  <select title="년도 선택">
    <option value="2019">2019</option>
    <option value="2018">2018</option>
  </select>
</span>

<hr>

<span class="select_custom select_type2">
  <select title="년도 선택">
    <option value="2019">2019</option>
    <option value="2018">2018</option>
  </select>
</span>
```



#### [공통] css

```css
.select_custom select {-webkit-appearance:none; -moz-appearance:none; appearance:none;} /* 화살표 없애기 */
.select_custom select::-ms-expand {display:none;} /* 화살표 없애기 for IE10, 11*/
```



#### [style1] 화살표를 background-image로 넣는 방법

```css
.select_type1 {display:inline-block; height:20px; border-radius:4px; background:#88422e; -moz-box-shadow:inset 0px 3px 3px #88422e; -webkit-box-shadow:inset 0px 1px 1px #88422e; vertical-align:middle}
.select_type1 select {width:100%; padding:0 35px 0 12px; height:20px; border:none; background:url('http://annecom.cafe24.com/_work/jazan/images/btn_select.png') no-repeat 100% 0; background-size:26px 20px; color:#fff; font-size:14px; line-height:19px; vertical-align:top;}
.select_type1 select option {color:#333}
```



#### [style2] 화살표를 border를 이용해 만드는 방법

```css
.select_type2 {display:inline-block; position:relative; height:20px; border:1px solid #ccc; background:#fff; vertical-align:middle}
.select_type2 select {position:relative; z-index:2; width:100%; padding:0 35px 0 12px; height:20px; border:none; background:transparent; font-size:14px; line-height:19px; vertical-align:top;}
.select_type2 select option {color:#333}
.select_type2::after {content:''; position:absolute; top:50%; right:5px; width:0; height:0; margin-top:-2px; border-style:solid; border-width:5px; border-color:#999 transparent  transparent  transparent}
```



#### Jsfiddle link

https://jsfiddle.net/sumim/43mupyb1/
