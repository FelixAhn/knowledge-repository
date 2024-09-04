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