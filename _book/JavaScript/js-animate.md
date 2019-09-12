## 자바스크립트 애니메이션 코드

jQuery를 이용해 텍스트의 각 문자마다 모션을 취하게 하는 코드.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
    <title>showNumber</title>
    <style>
        #numberArea .num {
            display: inline-block;
            opacity: 0;
        }
        #numberArea .num.show_number {
            opacity: 1;
            animation: showNumber 0.5s 1 ease-in-out;
        }
        @keyframes showNumber {
            0% {
                opacity: 0; 
                transform: translateY(20px)
            }
            100% {
                opacity: 1; 
                transform: translateY(0px)
            }
        }
    </style>
</head>
<body>
    <div id="numberArea"></div>
    <script type="text/javascript">
        $(document).ready(function(){
            showNumber("#numberArea","123,456,789");
        });
        function showNumber(target, value){
            $(target).text(value);
            var targetArr = [];
            for (i=0; i<value.length; i++){
                var sliceVal = value.slice(i, i+1);
                targetArr.push(sliceVal);
            } // 각 문자들을 for문을 이용해 배열 변수 안에 넣는다.
            $(target).html("");
            for (i=0; i<targetArr.length; i++){
                var idx = targetArr.length - (i+1);
                $(target).prepend("<span class='num'>" + targetArr[idx] + "</span>");
                // 배열 안에 들어간 문자들을 각각 span 태그로 감싼다.
                if (i == (targetArr.length - 1)){
                    $(target).find("span").each(function(j){
                        setTimeout(function(){
                            $(target).find("span:eq(" + (targetArr.length - (j+1)) + ")").addClass('show_number');
                        }, (j*50));
                    });
                };
                // for문의 조건식이 끝나면 각 span태그에 시간차를 두고 클래스를 추가하여 모션이 작동되도록 한다.
            };
        };
    </script>
</body>
</html>
```

