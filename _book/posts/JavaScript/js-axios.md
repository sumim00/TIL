# [JavaScript] axios

[axios](<https://www.npmjs.com/package/axios>) 는 Promise 기반 HTTP  클라이언트 라이브러리이다. 

axios를 사용하면 비동기 방식으로 데이터를 가져올 수 있으며, 브라우저와 Node.js 플랫폼 모두 사용 가능하다.



### 시작

- npm

  ```powershell
  $ npm install axios
  ```

- yarn

  ```powershell
  $ yarn add axios
  ```

- npm

  ```html
  <script src="https://unpkg.com/axios/dist/axios.min.js"></script>
  ```

  

### GET

```js
axios.get(url)
  .then(response => {
    console.log(response)
  })
  .catch(error => {
    console.log(error)
  })
```

