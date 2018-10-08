### 문제 1

양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

**내답변**
```js
// 원의반지름 * 원의 반지름 * 원주율
const area = (x) => {
  return x ** 2 * Math.PI;
} 
area(4)
```
### 문제 2

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

**내답변**
```js
function randomIntegervalue (min,max){
return  Math.floor(Math.random() * (max-min)) + min
}
randomIntegervalue(4,6)
```

### 문제 3

정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:
```
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

**내답변**
```js
function ceilBy5(num) {
  return Math.ceil(num/5) * 5
}
ceilBy5(32)
ceilBy5(37)
```

### 문제 4

배열을 입력받아, 요소들의 순서를 뒤섞은 새 배열을 반환하는 함수를 작성하세요.

**내답변**
```js
function randomArr(arr) {
  //배열 전체 복사
  let newArr = arr.slice();
  for (let item of newArr) {
    newArr.sort(() => Math.floor(Math.random() * newArr.length));
  }
  return newArr;
}

randomArr([1, 2, 3])
```
### 문제 5

임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

**내답변**
```js
function htmlColorCode (color){
  const numberRange = '0123456789abcdef';
  let colorCode =''; 
  for(let i=0; i<6; i++){
    colorCode += numberRange[Math.floor(Math.random() * numberRange.length)]
  }
return `#${colorCode}`
}
htmlColorCode();
```

### 문제 6

양수를 입력받아, 그 수만큼의 길이를 갖는 임의의 문자열을 반환하는 함수를 작성하세요.

**내답변**
```js
function randomLength (num){
  const str = 'abcdefghijklmnopqrstuvwxyz';
  let randomStr = '';
  for(let i = 0; i < num; i++ ){
    randomStr += str[Math.floor(Math.random() * str.length)]
  }
  return randomStr;
}
randomLength(4);
```

### 문제 7

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 표준편차를 구하는 함수를 작성하세요.

**선생님문제풀이**
```js
function stdDev(arr){
  // arr의 평균 구하기
  const sum = arr.reduce((acc, item) => acc+item, 0)
  const mean = sum /arr.length
  console.log(`mean: ${mean}`)
  // 각 요소에 대한 편차 구하기 (편차 = 값 - 평균)
  const ps = arr.map(item => item - mean)
  console.log(`ps: ${ps}`)
  // 각 요소에 대해 제곱하기 
  //  ** 2/* item 둘다 제곱 
  const powers= arr.map(item => item ** 2)
  console.log(`powers: ${powers}`)
  // 위 제곱한 배열의 평균 구하기
  const vv = powers.reduce((acc, item)=> acc + item,0)/powers.length
  console.log(`vv: ${vv}`)
  // 루트 씌우기
  return Math.sqrt(vv)
}

stdDev([1,2,3,4,5])
```