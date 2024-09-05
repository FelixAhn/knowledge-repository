## Event Listener & Event 객체
* Event Listener
```
- 마우스를 이용해서 버튼을 클릭할 때는 클릭"이벤트"가 발생
- 이벤트가 발생했을 때 어떠한 액션을 위한 함수 호출하는데 그 함수가 Event Listener

* addEventListener()
    - 어떠한 이벤트가 발생했을 때 이벤트 리스너를 호출하기 위해서는 이벤트 리스너를 해당 
      객체나 요소에 등록해줘야 함
```

* Event 객체 : 이벤트가 발생할 때 이벤트 객체를 가져올 수 있음
```javascript
// ex
const btn = document.querySelector(".btn")
btn.addEventListener('click', handleClick)

function handleClick(e) {
    let val;
    val = e;

    // Event target element
    val = e.target
    val = e.target.id
    val = e.target.className
    val = e.target.classList

    // Event type
    val = e.type

    // 원도우로부터 거리 좌표
    val = e.clientY
    val = e.clientX

    // 요소로부터의 거리 좌표
    val = e.offsetY
    val = e.offsetX
}
```

## Event종류
* UI 이벤트
```
- load : 문서나 객체가 로드 완료 되었을 때 발생
- change : 객체의 내용이 변동되거나 focus를 잃어을 때 발생
- resize : 객체의 크기가 바뀌었을 때 발생
- scroll : 스크롤바를 조작할 때 발생
- error : 에러가 발생했을 때 발생
```
* 키보드 이벤트
```
- keydown : 키를 눌렀을 때 발생
- keyup : 키를 눌렀다가 뗐을 때 발생
- keypress : 사용자가 눌렀던 키의 문자가 입력되었을 때 발생
```

* 마우스 이벤트
```
- click : 객체를 클릭 했을 때 발생
- dblclick : 객체를 더블클릭 했을 때 발생
- mousedown : 마우스를 클릭했을 때 발생
- mouseout : 마우스가 특정 객체 밖으로 나갔을 때 발생
- mouseover : 마우스가 특정 객체 위로 올려졌을 때 발생
- mousemove : 마우스가 움직였을 때 발생
- mouseup : 마우스에서 손을 뗏을 때 발생
```

* 포커스 이벤트
```
- foucs : 객체에 focus가 되었을 때 발생 
- blur : 객체가 focus를 잃었을 때 발생
```

* 폼 이벤트
```
- input : input, textarea 요소 값이 변경되었을 때 발생
- change : 선택 상자, 체크박스, 라디오 버튼의 상태가 변경되었을 때 발생
- select : 텍스트를 선택을 했을 때 발생
- reset : 리셋 버튼을 눌렀을 때 발생
- submit : 사용자가 버튼키 등을 활용하여 폼을 전송할 때 발생
- cut/copy/paste : 사용자가 폼필드의 콘텐츠를 잘라내기/복사/붙여 넣기 했을 때 발생
```

## Event Bubbling
```
- 이벤트 버블링이란 가장 깊게 중첩된 요소에 이벤트가 발생했을 때 이벤트가 위로 전달 되는 것을 의미
```
![event bubblig](/img/EB.png)
* 예시
```html
<div class="div1">
    div1
    <div class="div2">
      div2
      <div class="div3">
        div3
      </div>
    </div>
  </div>

<script>
    const divs = document.querySelectorAll('div')
    const handleDivClick = (e) => {
        console.log(e.currentTarget.className)
    }
    divs.forEach(div => {
        div.addEventListener('click', handleDivClick)
    });
</script>
```

* 예시 결과
```
div3
div2
div1

* 맨 아래에 위치한 div3를 클릭해서 이벤트가 발생을 하면 상위 요소에게 해당이벤트가 전달이 되면서 
  핸들러가 작동이 되는 흐름이 바로 이벤트 버블링!
```

* bubbling 중단하기
```
- 이벤트 버블링은 타깃 이벤트에서 시작해서 요소를 거쳐 document 객체를 만날 때 때까지 각 노드
  에서 모두 발생합니다. 몇몇 이벤트는 window 객체까지 거슬러 올라가기도 함
- 이것을 막기위해 event.stopPropagation()메소드를 사용
- 이러면 div3요소를 클릭해도 event bubbling이 발생하지 않기 때문에 부모 요소들의 핸들러 호출 x
```

## Event Capturing
```
- 이벤트 캡처링은 이벤트 버블링과 반대로 제일 상단에 있는 요소에서 아래로 이벤트가 내려옴
```
![event capturing](/img/EC.png)

* 예시
```html
<div class="div1">
    div1
    <div class="div2">
      div2
      <div class="div3">
        div3
      </div>
    </div>
  </div>

<script>
  const divs = document.querySelectorAll('div')

  const handleDivClick = (e) => {
    console.log(e.currentTarget.className)
  }

  divs.forEach(div => {
    div.addEventListener('click', handleDivClick, { capture: true 
    // default 값은 false
    })
  });
</script>
```

* 예시 결과
```
div1
div2
div3
```

## Event Delegation(이벤트 위임)
```
- 이벤트 위임이란 하위 요소마다 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트들을 
  제어하는 방식
- 이벤트 위임을 사용하면 요소마다 핸들러를 할당하지 않고, 요소의 공통 조상에 이벤트 핸들러를 
  단 하나만 할당해도 여러 요소를 한꺼번에 다룰 수 있음
```
* 예시
```html
<div id = "buttons">
    <button class="buttonClass">Click me</div>
    <button class="buttonClass">Click me</div>
</div>
<!-- 버튼이 2개 생기고 그 버튼들을 누르면 clicked라는 alert창이 뜨게 됨 -->
<script>
    const buttons = document.getElemetsByClassName("buttonClass")
    for (const button of buttons){
        button.addEventListener("click", () => alert("clicked"))
    }
</script>

<!-- 이렇게 생성하고 생성된 버튼을 누르면 alert창이 뜨지 않게 됨 이건 버튼이 생기기전에 
 각 버튼 요소에 핸들러가 더해졌기 때문. 새로 생긴 버튼요소에는 핸들거가 더해져있지 않음-->
<script>
    let buttonList = document.querySelector("#buttons")
    let button = document.createElement("button")

    button.setAttribute("class", "buttonClass")
    button.innnerText = "Click me"
    buttonList.appendChild(button)
</script>
```
* 해결책
    * 현재 상황은 하위 요소인 버튼에서 이벤트를 제어하고 있음
    * 새로운 아이템(하위요소)에 새로운 요소가 하나 더 추가 될 때마다 이벤트 리스너를 계속 등록해줘야함
    * 이 하위요소들이 존재하는 상위요소에서 이벤트를 제어하게 된다면 하위요소가 추가 될때 마다 따로<br>
      이벤트리스너를 등록하지 않아도 됨
    
    ```javascript
    const buttons = document.getElementById("buttons")
    buttons.addEventListener("click", () => alert("clicked"))
    ```
    * 이렇게 하면 모든 버튼에 다 이벤트 리스너를 추가하는 것이 아닌 버튼 상위요소인 div에 이벤트 리스너<br>
      를 추가해준 후에 하위에서 발생한 클릭 이벤트를 감지하게 됨 (이벤트 버블링을 통해서 감지)


