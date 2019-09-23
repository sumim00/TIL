## 해시 알고리즘 정리

해시 : key-value 쌍으로 데이터를 저장하는 자료구조.

### 1. 완주하지 못한 선수

> ###### 문제 설명
>
> 수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.
>
> 마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.
>
> ##### 제한사항
>
> - 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
> - completion의 길이는 participant의 길이보다 1 작습니다.
> - 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
> - 참가자 중에는 동명이인이 있을 수 있습니다.

```javascript
function solution(participant, completion) {
    participant.sort();
    completion.sort();

    for(let i in participant) {
        if(participant[i] !== completion[i]) return participant[i];
    }
}
```



### 2. 전화번호 

>  전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.
> 전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.
>
> - 구조대 : 119
> - 박준영 : 97 674 223
> - 지영석 : 11 9552 4421
>
> 전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.

```javascript
phone_book.sort();

for(int i = 0; i<phone_book.length-1; i++){
	if (phone_book[i].indexOf(phone_book[i+1]) !== -1){
	answer = false;
	break;
	}
})
```

접두어만 확인하기 때문에 sort()로 정렬한다.

if문으로 바로 다음 번호와 비교한 뒤, 일치하면 `answer` 변수값을 `false`로 변경하고 `break`로 빠져나오기.



### 3. 위장

> ###### 문제 설명
>
> 스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.
>
> 예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.
>
> | 종류 | 이름                       |
> | ---- | -------------------------- |
> | 얼굴 | 동그란 안경, 검정 선글라스 |
> | 상의 | 파란색 티셔츠              |
> | 하의 | 청바지                     |
> | 겉옷 | 긴 코트                    |
>
> 스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

```javascript
function solution(clothes) {
    return Object.values(
        clothes.reduce((obj, t)=> {
            obj[t[1]] = obj[t[1]] ? obj[t[1]] + 1 : 1;
            return obj;
        } , {})).reduce((a,b)=> a*(b+1), 1
    )-1;    
}
```

```javascript
function solution(clothes) {
    var answer = 1;
    var obj = {}            //중복되는 의상을 처리하기 위해 json 객체 사용
    clothes.forEach(function(element){
        if(obj[element[1]]>=1)    //중복되는 키 값이 존재할 때 +1
            obj[element[1]] +=1
        else                    //처음 등장하는 의상일 때 1로 초기화
            obj[element[1]] = 1
    })
    for(var x in obj)            //json 객체에 담긴 값으로 계산
        answer *= (obj[x]+1)
    return answer-1;
}
var clothes =[["crow_mask", "face"], ["blue_sunglasses", "face"], ["smoky_makeup", "face"]]
```



### 4. 베스트앨범

> ###### 문제 설명
>
> 스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.
>
> 1. 속한 노래가 많이 재생된 장르를 먼저 수록합니다.
> 2. 장르 내에서 많이 재생된 노래를 먼저 수록합니다.
> 3. 장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.
>
> 노래의 장르를 나타내는 문자열 배열 genres와 노래별 재생 횟수를 나타내는 정수 배열 plays가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.
>
> ##### 제한사항
>
> - genres[i]는 고유번호가 i인 노래의 장르입니다.
> - plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
> - genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
> - 장르 종류는 100개 미만입니다.
> - 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
> - 모든 장르는 재생된 횟수가 다릅니다.

```javascript
function solution(genres, plays) {
    var songs = 
        genres.map((genre, index) => {
            return {
                no: index,
                genre: genre,
                playCount: plays[index]    
            };
        });

    var genrePlayCount = [];
    songs.forEach(song => {
        var thisGenre = genrePlayCount.find(genrePlay => genrePlay.genre === song.genre);
        if (!thisGenre) {
            genrePlayCount.push({
                genre: song.genre, totalPlayCount: song.playCount
            });
        } else {
            thisGenre.totalPlayCount += song.playCount;
        }
    });

    genrePlayCount.sort((a, b) => b.totalPlayCount - a.totalPlayCount);

    var answer = [];
    genrePlayCount.forEach(genrePlay => {
        var thisGenreSongs = songs.filter(song => genrePlay.genre === song.genre);
        thisGenreSongs.sort((a, b) => b.playCount - a.playCount);
        answer.push(thisGenreSongs[0].no);
        if (thisGenreSongs.length > 1) {
            answer.push(thisGenreSongs[1].no);
        }
    });

    return answer;
}
```

