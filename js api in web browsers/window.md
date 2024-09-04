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