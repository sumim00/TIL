## MongoDB

>  https://www.mongodb.com/



MongoDB는 C++로 작성된 오픈 소스 문서 지향 데이터 베이스이다. 더불어 기존 SQL의 단점은 개선하되, 장점은 가져온 대표적인 NoSQL 서버 프로그램이다.



### 특징

#### Schemaless

스키마(Schema)란 를 조작하기 이전에 데이터의 구조, 표현방법, 관계 등을 미리 정의하는 일종의 청사진을 일컫는다. 기존에는 DBMS가 데이터를 조작하기 위해 스키마를 참조하여 명령을 수행했기 때문에 사전에 구조가 미리 정해져야하는데, 이러한 스키마가 없다는 것은 사전에 구조를 미리 정해놓지 않아도 DB를 조작할 수 있게 된 것이다.



#### 문서 지향적 (document-oriented) 

mongoDB는 기본적인 데이터를 Document로 부른다.  각 문서들은 MySQL과 같은 스키마가 고정된 구조 대신에 JSON 형태의 스키마형 문서를 사용하는데, 이를 BJSON(Binary JSON)이라고 부른다.

또한 Join 대신 Embedded document를 활용할 수 있다.







#### Querying (document-based query)

필터링, 수집, 정렬, 정규표현식 등 다양한 종류의 쿼리문을 지원한다.



#### Full Index Support

RDBMS인 MySQL에서 지원하는 대부분의 인덱싱을 제공한다. 이런 강력한 인덱스 기능 덕분에 빠른 쿼리 처리가 가능하다.



## Reference

https://nicewoong.github.io/development/2018/02/10/mongodb-feature/

https://sjh836.tistory.com/98

https://docs.mongodb.com/manual/introduction/

http://bigmatch.i-um.net/2013/12/09/mongodb%EB%A5%BC-%EC%93%B0%EB%A9%B4%EC%84%9C-%EC%95%8C%EA%B2%8C-%EB%90%9C-%EA%B2%83%EB%93%A4/

https://givemesource.tistory.com/82