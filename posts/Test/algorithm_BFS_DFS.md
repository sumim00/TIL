## 깊이 우선 탐색(DFS) / 너비 우선 탐색(BFS)

깊이 우선 탐색(DFS; Depth First Search)

-  스택(=선행관계)를 이용하여 그래프를 탐색하는 방법
- 나를 먼저 방문하고, 그 다음으로 인접한 노드를 차례로 방문 
- 스택을 이용해서 갈 수 있는 만큼 최대한 많이 가고 갈 수 없으면 이전 정점으로 돌아간다.

너비 우선 탐색(BFS; Breadth First Search)

- 큐를 이용해서 지금 위치에서 갈 수 있는 것을 모두 큐에 넣는 방식
- 큐에 넣을 때 방문했다고 체크해야 함.



### 1. 타겟 넘버

> ###### 문제 설명
>
> n개의 음이 아닌 정수가 있습니다. 이 수를 적절히 더하거나 빼서 타겟 넘버를 만들려고 합니다. 예를 들어 [1, 1, 1, 1, 1]로 숫자 3을 만들려면 다음 다섯 방법을 쓸 수 있습니다.
>
> ```
> -1+1+1+1+1 = 3
> +1-1+1+1+1 = 3
> +1+1-1+1+1 = 3
> +1+1+1-1+1 = 3
> +1+1+1+1-1 = 3
> ```
>
> 사용할 수 있는 숫자가 담긴 배열 numbers, 타겟 넘버 target이 매개변수로 주어질 때 숫자를 적절히 더하고 빼서 타겟 넘버를 만드는 방법의 수를 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한사항
>
> - 주어지는 숫자의 개수는 2개 이상 20개 이하입니다.
> - 각 숫자는 1 이상 50 이하인 자연수입니다.
> - 타겟 넘버는 1 이상 1000 이하인 자연수입니다.

```javascript
// 결과는 1 ± 1 ± 1 ± 1 ± 1 이므로 너비 우선 탐색으로 진행.
function solution(numbers, target) {
    let answer = 0;
    getAnswer(0,0);
    function getAnswer(x,value) {
        if(x<numbers.length){
            getAnswer(x+1,value + numbers[x]);
            getAnswer(x+1,value - numbers[x]);
        } else{
            if(value === target){
                answer++
            }
        }
    }
    return answer;
}
```



### 2. 네트워크

> ###### 문제 설명
>
> 네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.
>
> 컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.
>
> ##### 제한사항
>
> - 컴퓨터의 개수 n은 1 이상 200 이하인 자연수입니다.
> - 각 컴퓨터는 0부터 `n-1`인 정수로 표현합니다.
> - i번 컴퓨터와 j번 컴퓨터가 연결되어 있으면 computers[i][j]를 1로 표현합니다.
> - computer[i][i]는 항상 1입니다.

```javascript
function solution(n, computers) {
    var answer = 0;
    // 방문한 사실을 기록하고, 모든 노드를 방문하면 종료.
    var isVisited = [];
    for (var i = 0; i < n; i++){
        isVisited.push(false);
    }
    // 네트워크를 확인할 함수.
    function DFS (computers, i){
        if (isVisited[i]){return}
        isVisited[i] = true; // 확인 다 했으니 true로 변경
        
        for (var j = 0; j < n; j++){
            if (computers[i][j] == 1){
                DFS(computers, j)
            }
        }
    }
    
    // for문을 돌며 isVisited=false인 곳에서 DFS실행.
    for (var i = 0; i < n; i++){
        if (!isVisited[i]){
            answer++;
            DFS(computers, i)
        }
    }
    return answer;
}
```



### 3. 단어변환

> ###### 문제 설명
>
> 두 개의 단어 begin, target과 단어의 집합 words가 있습니다. 아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.
>
> ```
> 1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.
> 2. words에 있는 단어로만 변환할 수 있습니다.
> ```
>
> 예를 들어 begin이 hit, target가 cog, words가 [hot,dot,dog,lot,log,cog]라면 hit -> hot -> dot -> dog -> cog와 같이 4단계를 거쳐 변환할 수 있습니다.
>
> 두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한사항
>
> - 각 단어는 알파벳 소문자로만 이루어져 있습니다.
> - 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
> - words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
> - begin과 target은 같지 않습니다.
> - 변환할 수 없는 경우에는 0를 return 합니다.

```javascript
function solution(begin, target, words) {
    var answer = 0;
    function match(begin,x,c) {
        let count = 0;
        if(x<words.length){
            for(let i=0; i<begin.length; i++){
                if(begin[i] !== target[i]) count ++;
            }
            if(count>1){
                count=0;
                for(let i=0; i<begin.length; i++){
                    if(begin[i] !== words[x][i]) count++;
                    if(count > 1) break;
                }
                if(count>1) match(begin,x+1,c);
                else if(count === 1) match(words[x],x+1,c+1)
                else answer=c;
            }
            else if(count === 1) match(target,x+1,c+1);
            else answer = c;
        }else{
            if(begin === target) answer = c;
        }

    }
    match(begin,0,0);
    return answer;
}
```





### 4. 여행경로

> ###### 문제 설명
>
> 주어진 항공권을 모두 이용하여 여행경로를 짜려고 합니다. 항상 ICN 공항에서 출발합니다.
>
> 항공권 정보가 담긴 2차원 배열 tickets가 매개변수로 주어질 때, 방문하는 공항 경로를 배열에 담아 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한사항
>
> - 모든 공항은 알파벳 대문자 3글자로 이루어집니다.
> - 주어진 공항 수는 3개 이상 10,000개 이하입니다.
> - tickets의 각 행 [a, b]는 a 공항에서 b 공항으로 가는 항공권이 있다는 의미입니다.
> - 주어진 항공권은 모두 사용해야 합니다.
> - 만일 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로를 return 합니다.
> - 모든 도시를 방문할 수 없는 경우는 주어지지 않습니다.

```javascript
function solution(tickets) {
    var answer = [];
    DFS(tickets,'ICN',["ICN"]);
    // console.log(answer.sort());
    return answer.sort()[0];
    function DFS(t,start,str){
        // console.log("DFS t,start,str : ["+t+"],["+start+"],["+str+"]")
        if(t.length == 0){
            // console.log(str+"\n");
            answer.push(str)
        }
        for(var i in t){
            if(t[i][0] == start){
                let tmp = t.slice();
                tmp.splice(i,1);
                let tmp2 = str.slice();
                tmp2.push(t[i][1]);
                DFS(tmp,t[i][1],tmp2)
            }
        }
    }
}
```

