### 문제 1

두 수를 입력받아 큰 수를 반환하는 함수를 작성하세요.

```js
function larger(x,y){
  const a= x
  const b= y
  let c;
  // a가 크면 a를 c에 넣고, 아니면 b를 c에 넣는다.
  if (a>b){
    c=a
  } else{
    c=b
  }
  return c
}

function larger(x,y){
  let c;
  // a가 크면 a를 c에 넣고, 아니면 b를 c에 넣는다.
  if (x>y){
    c=x
  } else{
    c=y
  }
  return c
}

console.log(larger(3,2))
console.log(larger(3,6))

function larger(x,y){
  // return은 끝나면 바로 나오기 때문에 
  if (x>y){
    return x
  } else{
    return y
  }
}

// if else  연산자 ":"" 

```
### 문제 2

세 수를 입력받아 그 곱이 양수이면 `true`, 0 혹은 음수이면 `false`, 둘 다 아니면 에러를 발생시키는 함수를 작성하세요.

에러를 발생시키는 코드는 다음과 같습니다.

```js
throw new Error('입력값이 잘못되었습니다.');
```

```js
function isPositive(x,y,z) {
  if (x*y*z > 0) {
    return true
  } else if (x*y*z <= 0){
    return false
  } else {
    throw new Error('입력값이 잘못되었습니다.');
  }
}

console.log(isPositive(1,2,3))
console.log(isPositive(1,2,-3))
console.log(isPositive(1,2,'3'))

```
['throw 에러에 대한 설명'](https://helloworldjavascript.net/pages/175-control-statement.html)

### 문제 3

세 수 `min`, `max`, `input`을 입력받아, 다음과 같이 동작하는 함수를 작성하세요.
- `min`보다 `input`이 작으면, `min`을 반환합니다.
- `max`보다 `input`이 크면, `max`를 반환합니다.
- 아니면 `input`을 반환합니다.

예:
```
limit(3, 7, 5); -> 5
limit(3, 7, 11); -> 7
limit(3, 7, 0); -> 3
```

```js
function limit(min, max, input){
  if (min > input){
    return min
  } else if (max < input){
    return max
  } else{
    return input
  }
}

console.log(limit(3,7,5))
console.log(limit(3,7,11))
console.log(limit(3,7,0))
```

```
console.log vs return 
return은 반환, console.log은 출력 
```

### 문제 4

어떤 정수가 짝수인지 홀수인지 출력하는 함수를 작성하세요. 이를 이용해서, 1부터 20까지의 수가 각각 짝수인지 홀수인지 출력하는 프로그램을 작성하세요.

```js
function evenOrOdd(x){
  // 만약 x가 짝수면 'x: 짝수'라고 출력
  if (x%2=== 0){
    // 짝수 2 짝수  출력시 +를 넣어줘야되기 때문에 불편함으로 사용 하지 않음 
    // console.log('짝수'+ x +':짝수')
    console.log(x +':짝수')
  }else{
    // 요즘에 사용하는 방식
    // console.log(`홀수 ${x}:홀수`)
    console.log(`${x}:홀수`)
  }
  // 아니면 'x: 홀수'라고 출력
}

// 0부터 19까지 for문 
for (let i=0; i<20; i++){
  evenOrOdd(i + 1)
}
```

### 문제 5

100 이하의 자연수 중 3과 5의 공배수를 모두 출력하는 프로그램을 작성하세요.
```js
for (let i=0; i<100; i++){
  const num = i+1
  if ((num % 3 === 0 && num % 5 ===0 )){
     console.log(`${x} :공배수`)
  }else{
    console.log(`${x} :공배수가 아님`)
  }
}
```

### 문제 6

자연수를 입력받아, 그 수의 모든 약수를 출력하는 함수를 작성하세요.

```js
print(12)

// 1: 약수
// 5: 약수
```
```js
function print(input){
  for (let i=0; i<input; i++){
    const num = i + 1
    if (input % num === 0){
      console.log(`${num}: 약수`)
    }else {
      console.log(`${num}: 아님`)
    }
  } 
}
```

### 문제 7 (과제)

2 이상의 자연수를 입력받아, 그 수가 소수인지 아닌지를 판별하는 함수를 작성하세요.
**내답변**
```js
function isPrime(input){
    if (input<2){
      throw new("2이상의 자연수를 입력하시오")
    }else{
      for (let i=0; i<input; i++){
      const num = i+2;
      if (input % num === 0){
        return '소수가 아님'
      }
      return '소수'
    }
  }
}

isPrime(5);
```
**선생님문제풀이**
```js
function isPrime(x){
  // 소수: 1과 자기자신박에 약수가 없는 수
  //-> 1과 자기자신이 아닌 약수가 하나라도 있으면 소수가 아니다.
  for(let i = 2; i < x; i++){
    if (x % i ===0) {
      return false;
    }
  }
  return true;
}

isPrime(5);
```

### 문제 8

1부터 100까지의 수를 차례대로 출력하되, 자릿수에 3, 6, 9중 하나라도 포함되어 있으면 '짝!'을 대신 출력하는 프로그램을 작성하세요.

```js
1
2
짝! 
4
5
찍!
```
```js
function print(i){
  for (let i=0; i<100; i++){
    const num = i+1;
    if(num.toString().includes('3')||num.toString().includes('6')||num.toString().includes('9')){
    console.log(`짝!`)
    }else{
    console.log(`${num}`)
    }
  }
}

// includes 어쩔수 없지만 숫자를 문자열로 변경 하는것은 변수 선언
function print(i){
  for (let i=0; i<100; i++){
    const num = i+1;
    const str =num.toString();
    if(str.includes('3')||str.includes('6')||str.includes('9')){
    console.log(`짝!`)
    }else{
    console.log(`${num}`)
    }
  }
}

```

### 문제 9 (과제)

양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1을 입력받은 경우:
```
*
```

3을 입력받은 경우:
```
*
* *
* * *
```

5를 입력받은 경우:
```
*
* *
* * *
* * * *
* * * * *
```
**내답변**
```js
function startPrint(x){
  for(i=0; i<x; i++){
    const num = i + 1
    console.log('*'.padEnd(2).repeat(num));
  }
}
startPrint(5) 
```
**선생님문제풀이**
```js
function print(height){
  for (let i = 0; i <height; i ++){
    // 한 줄 출력
    let stars = ''
    for (let j = 0; j < i + 1; j++){
      //  별 표 하나를 출력
      stars += '* '
    }
    console.log(stars)
  }
}

function print(height){
  for (let i = 0; i <height; i ++){
    const stars ='* '.repeat(i + 1)
    console.log(stars)
  }
}

function print(height){
  for (let i = 0; i <height; i ++){
    console.log('* '.repeat(i + 1))
  }
}
```

### 문제 10 (과제)

양의 정수를 입력받아, 다음과 같은 패턴의 출력을 하는 함수를 작성하세요.

1를 입력받은 경우:
```
*
```

3를 입력받은 경우:
```
  *
 * *
* * *
 * *
  *
```

5를 입력받은 경우:
```
    *
   * *
  * * *
 * * * *
* * * * *
 * * * *
  * * *
   * *
    *
```
**내답변**
```js
function startTreePrint(x){
  for(i=0; i<x; i++){
    console.log(' '.repeat(x - i)+'*'.padEnd(2).repeat(i));
  }
    for(i=0; i<x; i++){
     console.log(' '.repeat(i)+'*'.padEnd(2).repeat(x - i));
  }
}
startTreePrint(5)
```
**선생님문제풀이**
```js
function printLine(height, i){
 const n = i + 1;
    const line = ' '.repeat(height - n) + '* '.repeat(n)
    console.log(line)
}

function print(height){
  for(let i = 0; i < height; i++){
    printLine(height, i)
  }
  for(let i = height -2; i >= 0; i--){
    printLine(height, i)
  }
}
print(3)
```
|i|n번쨰|공백|*|
|--|--|--|--|
|0|1|2|1
|1|2|1|2
|2|3|0|3

### 문제 11

두 수를 입력받아서, 두 수의 최대공약수를 반환하는 함수를 작성하세요. ([유클리드 호제법](https://ko.wikipedia.org/wiki/%EC%9C%A0%ED%81%B4%EB%A6%AC%EB%93%9C_%ED%98%B8%EC%A0%9C%EB%B2%95)을 참고하세요.)

```js
function euclidean (x,y){
 if (y == 0) {
   return x;
 }return (y, x%y)
}

euclidean(1071,1029)
```

### 문제 12

세 수를 입력받아 큰 것부터 차례대로 출력하는 함수를 작성하세요.

```js

```

### 문제 13

자연수 `n`을 입력받아, `n`번째 피보나치 수를 반환하는 함수를 작성하세요.
