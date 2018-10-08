### 문제 1

두 정수 `start`, `end`를 입력받아, `start`부터 `end`까지의 모든 정수를 배열로 반환하는 함수를 작성하세요.

예:
```
range(3, 6); -> [3, 4, 5, 6]
```
```js
function range(start, end) {
  // cosnt에 재대입만 불가능 한것 
  const arr = []
  // i에 변수 start
  // i <= end; false가 될때 루프 끝남
  for (let i = start; i <= end; i++) {
    arr.push(i)
  }
  return arr;
}

range(3, 6);
```
### 문제 2

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 합을 구하는 함수를 작성하세요.

```js
 function sum(arr){
  const arrIndex = arr;
  return arrIndex.reduce((acc, item)=> acc + item, 0);
 }

sum ([1,2,3])
```
```js
function sum(arr){
  let memory = 0;
  for(let i =0; i<arr.length; i++){
    memory += arr[i];
  }
  return memory
}
```

### 문제 3

배열을 입력받아, falsy인 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.
```js
function removeFalsy(arr){
  const newArr = []
  for (let i =0; i<arr.length; i++) {
    // ture이면 turely 이다
    if (arr[i]) {
      newArr.push(arr[i])
    }
  }
  return newArr
}

removeFalsy([0,1,NaN,3])
```

### 문제 4

배열을 입력받아, 중복된 요소가 제거된 새 배열을 반환하는 함수를 작성하세요.

```js
function removeDuplicates(arr){
  const newArr = []
  for (let i = 0; i<arr.length; i++) {
    if (!newArr.includes(arr[i])){
      newArr.push(arr[i])
    }
  }
  return newArr;
}

removeDuplicates('tommmmmmmmato');
```

### 문제 5

수 타입의 값으로만 이루어진 두 배열을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- 두 배열의 같은 자리에 있는 요소를 더한 결과가 새 배열의 요소가 됩니다.
- 만약 입력받은 두 배열의 길이가 갖지 않다면, 긴 배열에 있는 요소를 새 배열의 같은 위치에 포함시키세요.

예:
```
addArray([1, 2, 3], [4, 5, 6, 7]) -> [5, 7, 9, 7]
```
**내답변**
```js
function addArray(arr1, arr2){
  let longer 
  let sorter
  let toArray = [];
  if (arr1.length >arr2.length) {
    longer = arr1
    sorter = arr2
  } else {
    longer = arr2
    sorter = arr1
  }
console.log(longer);
console.log(sorter);
  for(let i =0; i < longer.length; i++){
    // null로 하면 안되는 이유는 ?? 
    if (sorter[i] !== undefined) {
      toArray.push(longer[i] + sorter[i])
      console.log(longer[i]);
    } else {
      toArray.push(longer[i])
      //  console.log(longer[i]);
    }
  }
  return toArray
}
addArray([1, 2, 3],[4, 5, 6, 7]) 
```
**선생님문제풀이**
```js
function addArray(arr1, arr2) {
  let longer
  let sorter
  // .slice()은 배열 복사 
  if (arr1.length > arr2.length) {
    // 원본 배열을 변경하지 않기 위해 사본을 만들어준다. 
    // 같은 값에 변수의 이름을 붙인것 
    longer = arr1.slice()
    sorter = [...arr2]
  } else {
    longer = arr2.slice()
    sorter = arr1.slice()
  }
  for (let i = 0; i < sorter.length; i++) {
    longer[i] = longer[i] + sorter[i]    
  }
  return longer
}
// 원본 배열이 바꿔버림.
addArray([1, 2, 3], [4, 5, 6, 7])
```

### 문제 6

배열을 입력받아, 배열의 요소 중 두 개를 선택하는 조합을 모두 포함하는 배열을 작성하세요.

예:
```
combination([1, 2, 3]); -> [[1, 2], [1, 3], [2, 3]]
```
**내답변**
```js
function combination (arr){
  let memory = [];
  // [i][j]
  for(let i = 0; i<arr.length; i++){
      for(let j = i+1; j<arr.length; j++){
        memory.push([arr[i],arr[j]]);
      }
  }
  return  memory;
}
combination([1, 2, 3]);
```
**선생님문제풀이**
```js
function combination (arr){
  let newArr = [];
  // [i][j]
  for(let i = 0; i<arr.length -1; i++){
      for(let j = i+1; j<arr.length; j++){
        newArr.push([arr[i],arr[j]]);
      }
  }
  return  newArr;
}
combination([1, 2, 3]);
```

### 문제 7

'금액'과 '동전의 종류가 들어있는 배열'를 입력받아, 최소한의 동전을 사용해서 금액을 맞출 수 있는 방법을 출력하는 함수를 작성하세요.
(단, 동전의 종류가 들어있는 배열에는 큰 동전부터 순서대로 들어있다고 가정합니다.)

예:
```
coins(263, [100, 50, 10, 5, 1]);
// 출력
100
100
50
10
1
1
1
```
**선생님문제풀이**
```js
function coins(input, coinTypes){
  // coinTypes를 내림차순 정렬
  coinTypes.sort((x,y)=> y-x)
  //남은 액수
  let remain = input
  // 현재 내가 보고있는 동전
  let currentIndex = 0;
  // 혹시 일어날지 모르는 코드는 방어적 코드라고 한다. 
  while(remain > 0 && currentIndex < coinTypes.length){
    // 남은 액수가 내가 지금 보고있는 동전보다 크거나 같으면
    if (remain >= coinTypes[currentIndex]) {
      console.log(coinTypes[currentIndex])
      remain -= coinTypes[currentIndex]
    } else {
      // 다음 동전으로 넘어간다. 
      currentIndex++
    }
  }
}

coins(263, [ 50, 100, 10, 5, 1 ]);
```

### 문제 8

수 타입의 값만 들어있는 배열을 입력받아, 해당 배열을 오름차순 정렬하는 함수를 작성하세요. (`Array.prototype.sort`를 사용하지 않고 작성해보세요. [선택 정렬](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%83%9D_%EC%A0%95%EB%A0%AC)을 참고하세요.)


