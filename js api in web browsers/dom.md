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

## DOM 탐색하기
```
- DOM을 이용하면 요소와 요소의 콘텐츠에 무엇이든 가능
- But, 무언가를 하기 전에 조작하고자 하는 DOM객체에 접근한느 것이 선행되어야 함
- DOM에 수행하는 모든 연산은 document객체에서 시작
- document 객체는 DOM에 접근하기 위한 "진입점"임
- 진입점을 통과하면 어떤 노드에도 접근 가능
```

## createElement
``` javascript
// createElement에 태그 이름을 넣으서 요소를 생성할 수 있음
document.createElement(tagName)

// *** 예제 ***
// element 생성
const li = document.crecreateElement("li")

// class 추가
li.className = "list-group-item"

// id 추가
li.id = "new-itme"

// attribute 추가
li.setAttribute("name", "New list item")

// 새로운 text node를 생성하고 더하기
li.appendChild(document.createTextNode("New list item"))

// li를 ul의 자식으로 더하기
document.querySelector("ul.list-group").appendChild(li);
```

## removeChild & replaceChild
```javascript
// 하나의 노드를 삭제
// 삭제할 때는 삭제 할 노드를 자식으로 가진 부모 노드에서 실행
parentNode.removeChild(node)

// 원래 있던 Child를 삭제하고 새 Child로 교체
// 교체할 때는 교체할 노드를 자식으로 가진 부모 노드에서 실행
parentNode.replaceChild(newChild, oldChild)
```