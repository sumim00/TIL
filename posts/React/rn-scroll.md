# [React Native] RN 스크롤,리스트 관련 컴포넌트 3가지

### ScrollView

내부의 요소가 스크롤이 가능하게 하는 컴포넌트. 화면에 표시되지 않는 요소 또한 렌더링되기 때문에 데이터의 양이 많을 경우에는 로딩에 시간이 많이 소요된다.

```react
<ScrollView>
    <Text>1</Text>
    <Text>2</Text>
    <Text>3</Text>
</ScrollView>
```



#### ListView

화면에 들어가는 요소가 많아질 때 사용하는 컴포넌트. ScrollView와는 달리 구조화된 데이터를 리스트로 표시한다는 특징이 있다. 

ListView를 사용 하기 위해서는 `dataSource `와 `renderRow` 2가지 props가 필요하다.

```react
<ListView
  dataSource={this.state.dataSource}
  renderRow={(rowData) => <Text>{rowData}</Text>}
/>
```



### FlatList

쉬운 리스트 렌더링을 위해 React Native v 0.43에 추가된 컴포넌트.

심플한 API와 다양한 퍼포먼스가 장점이다.

FlatList를 사용 하기 위해서는 `data`와 `renderItem` 2가지 props가 필요하다.

- data : 렌더링에 필요한 배열 요소
- renderItem : `data`로부터 가져온 데이터를 이용한 단일 리스트 아이템



```react
<FlatList
  data={[{key: 'a'}, {key: 'b'}]}
  renderItem={({item}) => <Text>{item.key}</Text>}
/>
```

