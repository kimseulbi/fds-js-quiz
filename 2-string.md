### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
// insensitiveEqual: 민감하지 않은 
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```

```js
function insensitiveEqual(str1,str2){
  const a= str1.toLowerCase();
  const b= str2.toLowerCase();
  if( a === b){
    return true;
  }else{
    return false;
  }
  // 삼항연산자 
  // return a===b ? true: false;
}
```

### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백을 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```
```
//공백 만들기 
' '.repeat(3)
```
```js
function leftPad(s, n){
  if (s.length < n) {
    const spaceNum = n - s.length
    return ' '.repeat(spaceNum) + s
  } else {
    return s
  }
}
leftPad('hello',8)
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

```js
function count(str){
  let num = 0;
  for(let i =0; i<str.length; i++){
    if(str[i]==='a' || str[i]==='e' || str[i]==='i' || str[i]==='o' || str[i]==='u'){
      // 검증
      // console.log('모음')
      num +=1
    } 
    // else {
    //   // 검증
    //   console.log('자음')
    // }
  }
  return num
}
```

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```
```js

```

### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

**선생님문제풀이**
```js
const isPalindrome = (input) => {
  // 구지 input.length을 다 돌릴 필요가 없기 때문에 input.length/2-1으로 변경 

  for (let i = 0; i < input.length; i++) {
    const left = i;
    const right = input.length - 1 - i;
    if (input[left] !== input[right]) {
     return false;
    }
  }
  return true;
}
isPalindrome('토마토마토');
```
### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```
**선생님문제풀이**
```js
const removeDuplicates = (input) => {
  let memory = ‘’;
  for (let i = 0; i < input.length; i++){
    if(memory.includes(input[i])) {
      continue;
    }else{
      memory += input[i]
    }
  }
  return memory
}

removeDuplicates(‘tomato’);
```
### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.

```js
const hideId = (input) => {
  const arr = input.split('@');
  console.log(arr);
  const id = '*'.repeat(arr[0].length);
  const domain = arr[1];
  console.log(id + '@' + domain);
}

hideId('seulxcxlcxcx@gmail.com')
```
**선생님문제풀이**
```js
const removeId = (input){
  let seen = false
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    //내가 지금 보고 있는 글자가 '@' 이면
    //seen의 값을 true로 바꾼다.
    if(input[i] === '@'){
      seen = true;
    }
    
    //seen이 true이면
    if(seen){
    //내가 지금 보고 있는 글자를 그대로 memory에 덧붙인다.
      memory += input[i]
    } else {
    //아니면, 별표를 대신 덧붙인다.
    memory += '*'
    }
  }
  //변환한 결과를 반환한다. 
  return memory;
}

const removeId2 = (input) => {
  // '@'을 기준으로 쪼갠 후
  const splitted = input.split('@')
  // id 부분과 같은 길이를 갖는 별표 문자열을 만든다.
  const stars = '*'.repeat(splitted[0].length)
  // 별표를 @, 도메인 부분과 이어붙인 후 반환한다.
  return stars + '@' + splitted[1]
}
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.
**내답변**
```js 
function swapCase(input) {
  let text = ''
  for (let i = 0; i < input.length; i++) {
    if (input[i] !== input[i].toLowerCase()) {
      // 소문자로 
      text += input[i].toLowerCase();
    } else {
      // 대문자로 변경하여라
      text += input[i].toUpperCase();
    }
  }
  // 반환값
  return text;
}
swapCase('JaveScript')
```
**선생님문제풀이**
```js
// 배열을 사용하지 않고, 루프를 사용해서 풀기
function swapCase(input) {
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    if (input[i].toUpperCase() === input[i]) {
      memory += input[i].toLowerCase()
    } else {
      memory += input[i].toUpperCase()
    }
  }
  return memory
}

swapCase('JavaScript')
```
```js
// 배열 메소드를 사용해서 풀기
//Array.form 배열 생성 문자열 하나씩 요소
const swapCase = input => Array.from(input)
// map 각요소에 함수를 적용 새로운 배열을 만듬
// 삼항 연산자로 true 이면 앞 false이면 뒤 
// join으로 배열을 문자열로 
  .map(c => c.toUpperCase() === c ? c.toLowerCase() : c.toUpperCase()).join('')

 swapCase('JaveScript')
```
### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
**내답변**
```js
function spelling(input) {
  const text = input.split(' ');
  let x = ''
  console.log(text);
  console.log(text.length);
  for (let i = 0; i < text.length; i++) {
    x += text[i][0].toUpperCase();
    console.log(x);
    for (let j = 1; j < text[i].length; j++) {
      x += text[i][j].toLowerCase();
      // [i] 숫자가 다르면 ''를 하시오 
    }
  }
  // 반환값
  return x
}
spelling('i am hungry')
```
**선생님문제풀이**
```js
// 배열을 사용하지 않고, 루프를 사용해서 풀기
function capitalize(input) {
  let seenBlank = true
  let memory = ''

  for (let i = 0; i < input.length; i++) {
    if (seenBlank) {
      memory += input[i].toUpperCase()
    } else {
      memory += input[i]
    }

    if (input[i] === ' ') {
      seenBlank = true
    } else {
      seenBlank = false
    }
  }

  return memory
}

capitalize('i am hungry')
```
```js
// 배열 메소드를 사용해서 풀기
// split 문자열을 특정 문자를 기준으로 잘라 새 배열 생성
const capitalize2 = input => input.split(' ')
// map으로 새로운 배열로 word 배열 생성 
// slice 인덱스 범위 지정으로 새로운 배열 
// 인덱스 0 부터 1 사이의 요소들을 대문자 변환 하여 배열 생성 
.map(word => word.slice(0, 1).toUpperCase() + word.slice(1)).join(' ')

capitalize2('i am hungry')
```
### 문제 11 (과제)

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)
**내답변**
```js
function longWord(input){
  const arr = input.split(' ');
  console.log(arr)
  let maxIndex = 0;
  for (let i=0; i < arr.length; i++){
    if (arr[maxIndex].length < arr[i].length){
      maxIndex = i;
    }
  }
  return arr[maxIndex];
}

longWord('i am hungry')
```
**선생님문제풀이**
```js
//아이디어: 한글자씩 보면서, 지금까지 봤던 단어중에 제일 긴단어를 기억해둔다. 
function longestWord(input) {
  let longest = ''// 지금까지 봤던 단어 중에 제일 긴단어
  let current = '' // 내가 지금보고 있는 단어
  for(let i = 0; i <input.length; i++) {
    //  내가 지금 보고 있는 글자가 공백이 아니면
    if (input[i] !== ' '){
      current += input[i]
      if (current.length >= longest.length){
        longest = current
      }
    } else {
      // 내가 지금 보고 있는 글자가 골백이면 
      // current를 처음부터 다시 시작
      current = ''
    }
  }
  return longest
}

longestWord('hello fun javascript')
```
```js
// 실무에서는 루프 보다는 배열을 더 많이 활용함 
// 배열 메소드 사용한 버전
function longestWord(input){
  const splitted = input.split(' ')
  // 작은 단위는 변수로 x,y를 사용 하지만 의미에 맞게 사용 하는것 좋다
  splitted.sort((x,y)=>y.length -x.length)
  return splitted[0]
}
longestWord('hello fun javascript')
```

### 문제 12 (과제)

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.
**내답변**
```js
const print = (str,num) => Array.from(str)
.slice(0,num).join('')

print ('javeScript',4)
```
**선생님문제풀이**
```js
function firstLetters(s,n) {
  // s.length가 n보다 클 경우
  if (s.length < n){
    return s;
  }
  // s.length가 n보다 작을경우
  let memory = ''
  for (let i = 0; i < s.length; i++){
    memory += s[i]
    if (memory.length === n) {
      return memory
    }
  }
}

firstLetters ('javeScript',15)
```

### 문제 13 (과제)

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

배열을 순회할때 순회중인 배열을 바꾸면 안된다.
**내답변**
```js
function change (input){
  let memory = '';
  for(i=0; i<input.length; i++){
    if (input[i] === input[i].toUpperCase()){
      // 대문자 앞에 _를 넣어라 
      memory += '_'+ input[i].toLowerCase()
    } else {
      memory += input[i]
    }
  }
  return memory;
}
change('javeScript')
```
**선생님문제풀이**
```js
경우 바로 앞에 밑줄을 쳐준다.
function toSnakeCase(input) {
  let memory = ''
  for (let i=0; i<input.length; i++){
    // 만약, 첫글자가 아닌 대문자를 만났을 경우
    if (i !== 0 && (input[i].toUpperCase() === input[i])){
      memory += '_'
    }
    memory += input[i].toLowerCase()
  }
  return memory
}

toSnakeCase('JavaScript')
```

### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

### 문제 15 (과제)

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```
**내답변**
```js
const split = (str,cut) => {
  const arr = [];
  let index = 0;
  for (let i = 0; i< str.length; i++){
    if (str[i] === cut){
      arr.push(str.slice(index,i))
      index = i + 1;
    }else if (i === str.length - 1){
      arr.push(str.slice(index, str.length))
    }
  }
  return arr;
} 

split('Hello World');
split('Hello World', ' ');
split('let,const,var', ','); 
```
**선생님문제풀이**
```js
function split (input, sep){
  //'seoarator'
  //현재 보고 있는 단어 
  let memory = ''
  let arr = []
  for (let i = 0; i <input.length; i++) {
    if (input[i] !== sep) {
      memory += input[i]
    } else {
      arr.push(memory)
      memory = ''
    }
  }
  arr.push(memory)
  return arr
}

split('let,const,var', ','); 
```

### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
