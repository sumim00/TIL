# SVG

SVG란 확장 가능한 벡터 그래픽(Scalable Vector Graphics)의 약어로, 그래픽을 마크업하기 위한 W3C XML의 특수언어이다.

ie8 이전 버전을 제외한 대부분의 주요 웹 브라우저들은 SVG를 지원한다. ie8 이전 버전에서 SVG 파일을 보기 위해서는 별도의 플러그인을 설치해야 한다. 



## 시작하기

```svg
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">

  <rect width="100%" height="100%" fill="red" />

  <circle cx="150" cy="100" r="80" fill="green" />

  <text x="150" y="125" font-size="60" text-anchor="middle" fill="white">SVG</text>

</svg>
```

`<svg/>`는 SVG 도형을 감싸는 루트 요소다. 유효성 검사를 위해 `version` 속성과 `baseProfile` 속성을 설정해야 한다. 

`<svg/>`태그 안에 작업할 구성요소를 삽입한다. ` <rect/>`는 사각형, `<circle/>`은 원, `<text/>`는 텍스트를 렌더한다.



## 기본 도형

- 사각형 `<rect/>`
- 원 `<circle/>`
- 타원 `<ellipse/>`
- 선 `<line/>`
- 직선들의 그룹 `<polyline/>`
- 다각형 `<polygon/>`
- 패스 `<path/>`



### 사각형 `<rect/>`

```svg
<rect x="10" y="10" rx="10" ry="10" width="30" height="30"/>
```

- `x`, `y` - 사각형의 좌측 상단의 x, y 값

- `rx`, `ry` - 사각형의 둥근 꼭짓점의 x 방향으로의 반지름
- `width`, `height` - 사각형의 너비와 높이



### 원 `<circle/>`

```svg
<circle cx="25" cy="75" r="20"/>
```

- `r` -  원의 반지름
- `cx`, `cy` - 원의 중심 중 x, y값



### 타원 `<ellipse/>`

```svg
<ellipse cx="75" cy="75" rx="20" ry="5"/>
```

- `rx`, `ry` - 타원의 x,y방향으로의 반지름의 길이
- `cx`, `cy` - 타원의 중심 중 x,y값



### 선 `<line/>`

```svg
<line x1="10" y1="110" x2="50" y2="150"/>
```

- `x1` - 시작 지점의 x값
- `y1` - 시작 지점의 y값
- `x2` - 끝 지점의 x값
- `y2` - 끝 지점의 y값



### 직선들의 그룹 `<polyline/>`

```svg
<polyline points="60 110, 65 120, 70 115, 75 130, 80 125, 85 140, 90 135, 95 150, 100 145"/>
```

- `points` - 각 지점 별 x, y 좌표들의 값



### 다각형 `<polygon/>`

```svg
<polygon points="50 160, 55 180, 70 180, 60 190, 65 205, 50 195, 35 205, 40 190, 30 180, 45 180"/>
```

- `points` - 각 지점 별 x, y 좌표들의 값
- 마지막 지점과 첫 번째 지점을 연결하여 닫힌 모양을 만든다는 점에서  `<polyline/>`과 다르다.



### 패스 `<path/>`

```svg
<path d="M 20 230 Q 40 205, 50 230 T 90230"/>
```

- `d` - 지점의 위치 및 패스에 대한 정보가 담겨 있다. 





## Refer

[SVG 튜토리얼 - SVG | MDN](<https://developer.mozilla.org/ko/docs/Web/SVG/Tutorial>)

[스케일러블 벡터 그래픽스 - 위키백과, 우리 모두의 백과사전]([https://ko.wikipedia.org/wiki/%EC%8A%A4%EC%BC%80%EC%9D%BC%EB%9F%AC%EB%B8%94_%EB%B2%A1%ED%84%B0_%EA%B7%B8%EB%9E%98%ED%94%BD%EC%8A%A4](https://ko.wikipedia.org/wiki/스케일러블_벡터_그래픽스))

