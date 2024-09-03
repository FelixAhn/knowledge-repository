## 자바스크립트의 `var`, `let`, `const` 비교

| 특성                   | `var`            | `let`            | `const`          |
|------------------------|------------------|------------------|------------------|
| **중복선언 가능 여부**     | 가능             | 불가능            | 불가능            |
| **재할당 가능 여부**     | 가능             | 가능             | 불가능            |
| **블록 스코프**          | X (함수 스코프)  | O (블록 스코프)  | O (블록 스코프)  |
| **초기화 필요 여부**     | 초기화 없이 선언 가능 | 초기화 없이 선언 가능 | 선언과 동시에 초기화 필요 |
| **호이스팅**             | O (선언과 초기화 분리) | O (선언만 호이스팅, 초기화는 X) | O (선언만 호이스팅, 초기화는 X) |

## var, let, const 예시
* var
```javascript
var greeting = "hello";
console.log(greeting); // hello

var greeting = "hi";   
console.log(greeting); // hi

greeting = "how are you>?";
console.log(greeting); // how are you?
```
* let
```javascript
let greeting = "hello";
console.log(greeting); // hello

let greeting = "hi";   
console.log(greeting); // error(중복선언 불가능)

greeting = "how are you>?";
console.log(greeting); // how are you? (재할당 가능)
```

* const
```javascript
const greeting = "hello";
console.log(greeting); // hello

const greeting = "hi";   
console.log(greeting); // error(중복선언 불가능)

greeting = "how are you>?";
console.log(greeting); // error(재할당 불가능)
```

* 예외
```javascript
// const로 선언했어도 배열과 객체의 값을 변경하는 것은 가능
const arrayList = [1, 2, 3];
arrayList.push(4);
console.log(arrayList);

const objectList = {a: "a", b: "b"}
objectList.c = "c"
console.log(objectList);
```

## 블록스코프?
```
 - 변수나 함수가 정의된 코드 블록 내에서만 접근할 수 있도록 제한된 스코프(유효 범위)를 의미

  * let, const: 블록 스코프를 따름. 블록 밖에서는 접근x
  * var: 함수 스코프를 따르기 때문에 블록을 무시하고 함수 내 어디서든 접근 가능
```

## 블록스코프 예시
* let , const
```javascript
function func(){
  if (true){
    let a = "a";
    console.log(a); // a
  }
  console.log(a);   // 참조 error
}

console.log(a);     // 참조 error
```
* var
```javascript
function func(){
  if (true){
    var a = "a";
    console.log(a); // a
  }
  console.log(a);   // a
}

console.log(a);     // 참조 error
```

## 호이스팅?
```
 - 자바스크립트에서 변수, 함수 선언이 해당 코드가 실제로 실행되기 전에 최상단으로 
   "끌어올려지는" 것처럼 동작하는 메커니즘
```

* var 선언문의 호이스팅
```javascript
console.log(greeting);  // undefined

var greeting = "hello";
```

* 함수 선언문의 호이스팅
```javascript
func(); // hoisting test

function func() {
  console.log("hoisting test");
}
```

* let, const 선언문이 호이스팅 : let과 const도 여전히 호이스팅이 되지만 초기에 어떤 값도 할당되지 않음
```javascript
console.log(greeting);  // 참조 error

const greeting = "hello";
```
* 변수는 초기에 undefined로 초기된 var와 달리 초기에 초기화 되지 않아 코드가 실행 되면 변수에 값을 할당하기
전에 console.log가 발생하여 위의 오류가 발생 이러한 일이 발생하는 이유를 `TDZ(Temporal Dead Zone)`이라고 한다. 일시적 데드 존은 변수를 사용할 수 없는일시적인 비활성 상태를 나타낸다.

## Console 객체
```
 - console 객체는 브라우저의 디버깅 콘솔에 접근할 수 있는 메서드를 제공
 - 아무 전역 객체에서나 접근 가능
 - 브라우징 문맥에선 Window, 워커에서는 WorkerGlobalScope(en-US)가 속성으로 포함
 - Window.console의 형태로 노출되어 있어 간단하게 console로 참조 가능
 ```

 ## 자바스크립트 타입
 * 기본적으로 javascript는 `원시타입`에 대한 `값을 저장하기 위해 Call Stack 메모리 공간`을 사용하지만
 `참조 타입`의 경우 `Heap이라는 별도의 메모리 공간을 사용`, 이 경우 `Call Stack`은 개체 및 배열 값이 아닌
 `Heap 메모리 참조 ID`를 값으로 저장
 * 원시타입(불변성) : 고정된 크기로 Call Stack 메모리에 저장, 실제 데이터가 변수에 할당
```
 - Boolean : true와 false의 값을 가짐
 - String : 문자열을 나타냄
 - Number : 숫자 값을 나타냄
 - null : 하나의 값을 가짐, 의도적으로 "값이 없음" 을 나타내기 위해서 사용
 - undefined : 하나의 값을 가짐, 초기화되지 않은 변수의 기본값으로 설정
 - Symbol : 변경 불가능한 유일한 값을 생성할 때 사용, 값 자체의 확인이 불가하여 외부 노출x (ES6)
 ```

 * 참조 타입 : 데이터크 크기가 정해지지 않고 Call Stack 메모리에 저장, 데이터의 값이 heap에 저장되며
             변수에 heap 메모리의 주소값이 할당
 ```
 - Object : 객체
 - Array : 배열
 - Fucntion : 함수
 - Classes : 클래스
 ```


## 자바스크립트의 동적 타입
* 자바스크립는 느슨한 타입의 동적 언어이다. 변수는 어떤 특정 타입과 연결되지 않으며 모든 타입의 값으로 할당
및 재할당이 가능하다.
```javascript
let foo = 42 // number 
foo = "bar"  // string
foo = true   // boolean
```

## 자바스크립트의 타입 변환
* 문자열 변환
```javascript
let val;

val = String(111);
val = String(8 + 4);
val = String(false);
val = String(new Date());
val = String([1, 2, 3, 4]);

// toStirng 이용
val = (5).toString();
val = (true).toString();
```

* 숫자 변환
```javascript
let val;

val = Number("1");
val = Number(true);
val = Number(null);
val = Number("hello");
val = Number([1, 2, 3]);

val = parseInt("111.40")   // 111
val = parseFloat("111.40") // 111.4
val.toFixed(2)             // 111.40
```

* 자바스크립트 자체에 의해 자동으로 변환
```javascript
const val1 = 2;
const val2 = 3;
const sum = val1 + val2;

console.log(sum);        //5
console.log(typeof sum); // number
```

* string 1, number 1일 때
```javascript
const val1 = String(2);
const val2 = 3;
const sum = val1 + val2;

console.log(sum);         // 23
console.log(type of sum); // string
```

## Math 객체
```javascript
let val;

val = Math.E
val = Math.PI
val = Math.SQRT2
val = Math.SQRT1_2
val = Math.LN2
val = Math.LN10
val = Math.LOG2E
val = Math.LOG10E

val = Math.round(2.4)
val = Math.ceil(2.4);
val = Math.floor(2.8);
val = Math.abs(-2);
val = Math.sqrt(64);
val = Math.pow(8, 2);
val = Math.min(2, 3, 5, 7, 11, 6, 8 , -1);
val = Math.max(2, 3, 5, 7, 11, 6, 8 , -1);
val = Math.random();

val = Math.floor(Math.random() * 20 + 1);
```

## 템플릿 리터럴
* 백틱을 사용하여 문자열을 표현한 것
```javascript
const a = 5;
const b = 10;
// ES5
"string text line 1\n" + "string text line 2"
"Fifteen is" + (a + b) + "and\nnot" + (2 * a + b) + "."

// ES6
`string text line 1
string text line2`
`Fifteen is ${a+b} and not ${2*a+b}.`
```

## 루프
* 루프 종류
```
- for : 코드 블록을 여러 번 반복
- for/in : 객체의 속성에 따라 반복
- while : 지정된 조건이 true인 동안 코드 블록 반복
- do/while : while루프의 변형, 이 루프는 조건이 true인지 검사하기 전에, 코드 블록을 한 번 실행,
             그러고 나서 조건이 true인 동안 루프 반복
```

* Ex) for
```javascript
for(let i = 0; i < 10; i++){
  if (i === 3){
    console.log("IT is 3");
    continue;
  }
  
  if (i === 5){
    console.log("IT is 5");
    break;
  }
}
```

* Ex) for/in
```javascript
const user = {
  name : "Han",
  province: "경기도",
  city : "성남시"
}

for(let x in user){
  console.log(`${x} : ${user[x]}`);
}
```

* Ex) while
```javascript
let i = 0;

while(i < 10){
  console.log(i);
  i++;
}
```

* Ex) do/while
```javascript
let i = 0;

do {
  console.log(i);
  i++;
}
while(i < 10);
```

### FOREACH / MAP
* Ex) FOREACH / Map
```javascript
const loactions = ["서울", "부산", "경기도", "대구"];

loactions.forEach(function (loaction, index, array) {
  console.log(`${index} : ${loaction}`);
  console.log(array);
})
// 0 : 서울
// ["서울", "부산", "경기도", "대구"]
// ... 5까지 진행

loactions.map(function(loaction) {
  console.log(loaction);
})
// 서울
// 부산
// 경기도
// 대구
```

* for와 for each의 차이점
```
- for 루프는 원래 사용되었던 접근 방식이지만 forEach는 배열 요소를 반복하는 새로운 접근 방식
- for 루프는 필요한 경우 break문을 사용하여 for루프를 중단할 수 있지만 for each에서는 이
  와 같은 작업 불가능
- for 루프는 await와 함께 작동하지만 for each는 await와 완벽하게 동작 x
- for 루프를 사용한 성능이 for each 루프보다 좋음
```

## Window 객체
```
- window 객체는 브라우저에 의해 자동으로 생성되며 웹 브라워저의 창을 나타낸다
- * window은 브라우저 객체이지 javascript의 객체가 아니다!
- 브라우저의 창에 대한 정보를 알 수 있고, 이 창을 제어할 수 있다
- var 키워드로 변수를 선언하거나 함수를 선언하면 window 객체의 프로퍼티가 된다
```
* 사용 예시
```javascript
// Alert
alert("hello world!");

// Prompt
const input = prompt();
alert(input);

// Confirm
if(confirm("yes or no")){
  console.log('yes')
}
else{
  console.log('no')
}

let val;

// Outter heigth and width
val = window.outerHeight
val = window.outerWidth

// Inner heigth and width
val = window.innerHeight
val = window.innerWidth

// Scroll points
val = window.scrollY
val = window.scrollX

// Location Object
val = window.loaction
val = window.loaction.hostname
val = window.loaction.port
val = window.loaction.href
val = window.loaction.search

// Redirect
window.loaction.href = "http://naver.com"
// Reload
window.loaction.reload()

// Histroy Objecgt
window.history.go(-2)
val = window.histroy.length

// Navigator Object
val = window.navigator
val = window.navigator.userAgent
val = window.navigator.Language

// Browser Object Model (BOM)
window.loaction
window.navigator
window.history
window.screen

// Document Object Model (DOM)
window.documnet
```
* var로 선언해서 window 객체의 프로퍼티 만들기
```javascript
// let과 const는 블록 스코프이기에
// window 객체 내부의 블록에서 선언된 것으로 전역 객체 프로퍼티로 활용x
var greeting = "hello"

function doGreeting() {
  return greeting
}

console.log(window.greeting)      // hello
console.log(window.doGreeting())  // hello
```

## DOM(Document Obejct Model)
```
- DOM은 메모리에 웹 페이지 문서 구조를 트리구조로 표현해서 웹 브라우저가 HTML 페이지를
  인식하게 해줌
- 웹페이지를 이루는 요소들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리 구조로 만든
  객체 모델을 의미
```
![domtree](/img/dom.png)

* DOM조작 예시
```html
<button class="btn">Click</button>
```
```javascript
var btn = document.querySelector(".button")

btn.onClick = function() {
  this.style.backgroundColor = "red"
}
```

* 웹 페이지 빌드 과정(Critical Rendering Path CRP)
```
- 브라우저가 서버에서 페이지에 대한 HTML응답을 받고 화면에 표시하기 전에 여러
  단계가 존재
- 웹 브라우저가 HTML 문서를 읽고, 스타일을 입히고 viewport에 표시하는 과정
```
![CRP](/img/CRP.png)

* CSS 객체 모델 (CSSOM)
```
- CSS 객체 모델은 javascript에서 css를 조작할 수 있는 API집합
- HTML 대신 CSS가 대상인 DOM이라고 생각할 수 있으며, 사용자가 CSS 스타일을 동적으로 
  읽고 수정할 수 있는 방법
```

## innerHTML, innerText, textContext의 차이 (알아두면 좋은 지식)
```javascript
const e = document.getElementById('e');

console.log(e.innerHTML)
console.log(e.innerText)
console.log(e.textContext)
```
```
- innerHTML : html까지 같이 보여줌
- innerText : 사용자에게 보여지는 텍스트 값을 읽어오며 여러 공백을 무시하고 하나의 공백
              만 처리
- textContext : display:none 스타일이 적용된 숨겨진 텍스트도 가져옴
                노드가 가지고 있는 텍스트 값 그대로를 보여줌
```

