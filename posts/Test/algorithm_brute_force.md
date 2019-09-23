## 완전탐색 알고리즘 문제 정리

### 1. 모의고사

> ###### 문제 설명
>
> 수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.
>
> 1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
> 2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
> 3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...
>
> 1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한 조건
>
> - 시험은 최대 10,000 문제로 구성되어있습니다.
> - 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
> - 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요

```javascript
function solution(answers) {
    var answer = [];
    // 수포자 배열 정의
    var al = [1, 2, 3, 4, 5];
    var a2 = [2, 1, 2, 3, 2, 4, 2, 5];
    var a3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5];
    
    // 풀은 문제 
    var a1c = answers.filter((a, i) => a === al[i%al.length]).length;
    var a2c = answers.filter((a, i) => a === a2[i%a2.length]).length;
    var a3c = answers.filter((a, i) => a === a3[i%a3.length]).length;
    
    // max값
    var max = Math.max(a1c, a2c, a3c);
    
    // 각 확인 후 출력
    if (a1c === max){answer.push(1)}
    if (a2c === max){answer.push(2)}
    if (a3c === max){answer.push(3)}
    
    return answer;
}
```



### 2. 소수 찾기

> ###### 문제 설명
>
> 한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.
>
> 각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.
>
> ##### 제한사항
>
> - numbers는 길이 1 이상 7 이하인 문자열입니다.
> - numbers는 0~9까지 숫자만으로 이루어져 있습니다.
> - 013은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.

```javascript
function solution(numbers) {
    const nums = numbers.split("")
    const max = Number(nums.slice().sort((x, y) => y - x).join(""))
    const primeArr = primes(max)
    let count = 0
    for (const item of primeArr) {
        const arr = item.toString().split("")
        if (isTrue(arr, nums)) count++
    }
    return count
}

const isTrue = (arr, nums) => {
    const copy = nums.slice()
    for (const item of arr) {
        const index = copy.indexOf(item)
        if (index === -1) {
            return false
        }
        copy.splice(index, 1)
    }
    return true
}

const primes = max => {
  const arr = [2];
  for (let i = 3; i <= max; i += 2) {
    let isPrime = true;
    const sqrt = Math.sqrt(i);
    for (const item of arr) {
      if (item > sqrt) {
        break;
      }
      if (i % item === 0) {
        isPrime = false;
        break;
      }
    }
    if (isPrime) arr.push(i);
  }
    return arr
}
```



### 3.숫자 야구

> ###### 문제 설명
>
> 숫자 야구 게임이란 2명이 서로가 생각한 숫자를 맞추는 게임입니다. [게임해보기](https://scratch.mit.edu/projects/131352991/)
>
> 각자 서로 다른 1~9까지 3자리 임의의 숫자를 정한 뒤 서로에게 3자리의 숫자를 불러서 결과를 확인합니다. 그리고 그 결과를 토대로 상대가 정한 숫자를 예상한 뒤 맞힙니다.
>
> ```
> * 숫자는 맞지만, 위치가 틀렸을 때는 볼
> * 숫자와 위치가 모두 맞을 때는 스트라이크
> * 숫자와 위치가 모두 틀렸을 때는 아웃
> ```
>
> 예를 들어, 아래의 경우가 있으면
>
> ```
> A : 123
> B : 1스트라이크 1볼.
> A : 356
> B : 1스트라이크 0볼.
> A : 327
> B : 2스트라이크 0볼.
> A : 489
> B : 0스트라이크 1볼.
> ```
>
> 이때 가능한 답은 324와 328 두 가지입니다.
>
> 질문한 세 자리의 수, 스트라이크의 수, 볼의 수를 담은 2차원 배열 baseball이 매개변수로 주어질 때, 가능한 답의 개수를 return 하도록 solution 함수를 작성해주세요.

```javascript
function solution(baseball) {
    var answer = 0;

    // 서로 다른 3개의 수 조합. 
    for(let i=123; i<=987; i++) {
        let [x, y, z] = (i+"").split('');

        // 각 수의 범위는 1~9 
        if(x === "0" || y === "0" || z === "0") continue;
        if(x === y || x === z || y === z) continue;

        for(let j=0; j<baseball.length; j++) {
            let strike = 0;
            let ball = 0;

            const [query, query_s, query_b] = baseball[j];
            const [query_x, query_y, query_z] = (query + "").split('');
            if(query_x === "0" || query_y === "0" || query_z === "0") break;
            if(query_x === query_y || query_x === query_y || query_y === query_z) break;

            if(x === query_x) strike++;
            if(y === query_y) strike++;
            if(z === query_z) strike++;
            if(query_s != strike) break;

            if((x === query_y) || (x === query_z)) ball++;
            if((y === query_x) || (y === query_z)) ball++;
            if((z === query_x) || (z === query_y)) ball++;
            if(query_b != ball) break;

            if(j === baseball.length - 1) answer++;
        }
    }


    return answer;
}
```



### 4. 카펫

> ###### 문제 설명
>
> Leo는 카펫을 사러 갔다가 아래 그림과 같이 중앙에는 빨간색으로 칠해져 있고 모서리는 갈색으로 칠해져 있는 격자 모양 카펫을 봤습니다.
>
> ![image.png](https://grepp-programmers.s3.amazonaws.com/files/ybm/7c94563a35/2ff27ac9-97d0-43a9-9cf8-a344b8e7912e.png)
>
> Leo는 집으로 돌아와서 아까 본 카펫의 빨간색과 갈색으로 색칠된 격자의 개수는 기억했지만, 전체 카펫의 크기는 기억하지 못했습니다.
>
> Leo가 본 카펫에서 갈색 격자의 수 brown, 빨간색 격자의 수 red가 매개변수로 주어질 때 카펫의 가로, 세로 크기를 순서대로 배열에 담아 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한사항
>
> - 갈색 격자의 수 brown은 8 이상 5,000 이하인 자연수입니다.
> - 빨간색 격자의 수 red는 1 이상 2,000,000 이하인 자연수입니다.
> - 카펫의 가로 길이는 세로 길이와 같거나, 세로 길이보다 깁니다.

```javascript
function solution(brown, red) {
    var answer = [];
    for (var i = 3; i <= (brown+red)/i; i++) {
        var x = Math.floor((brown+red)/i);
        if( (x-2)*(i-2)=== red) {
            break;
        }
    }

    return [x,i];
}
```

