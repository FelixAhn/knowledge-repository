### CSS?
```
사용자에게 문서를 표시하는 방법을 지정하는 연어
```

### CSS 사용 방법 종류
```
 - 인라인 스타일 : HTML 안에서 Style속성을 이용하는 방법
 - 내부 스타일 시트 : <style>태그를 통해서 HTML 문서 내부에서 이용하는 방법
 - 외부 스타일 시트 : 별도 CSS 파일을 HTMl의 문서에 연결하는 방법

 * 우선순위 : 인라인 > 내부, 외부, > 웹 브라우저 기본
```

### CSS 기본 구조
```
 - 선택자 : CSS적용할 HTML요소 가르킴
 - 프로퍼티 : 무엇을 바꿀지 결정
 - 값 : 프로퍼티 지정한 것을 얼마나 바꿀지 결정
```

### CSS 수치 값 종류
```
 - px
 - %
 - em, rem (환경에 따라 변하는 단위)
    * em : 같은 엘리먼트에서 지정된 기준으로 표시, 없다면 상위 요소
    * rem : 최상위 엘리먼트에 지정된 기준으로 표시
```

### CSS Transition
```
 - 사용법 : transition: <property> <duration>

 - 종류 
    * ease : 기본값, 느리게 시작 => 빠르게 전환 => 느리게 종료
    * linear : 균일하게 전환
    * ease-in : 가속, 느린 시작 => 빠른 끝
    * ease-out : 감속, 빠른 시작 => 느린 끝
    * ease-in-out : 느린 시작 => 느린 끝
    * cubic-bezier(n,n,n,n) : 3차 배지어 함수에 자신의 임의로 지정
```

### CSS 가상 클래스(pseudo-class)와 가상 요소(pseudo-element)
```
 - 가상 클래스 : 별도의 class지정 없이 지정한 것처럼 요소 선택가능
 - 가상 요소 : 가상 클래스처럼 선택자에 추가, 존재하지 않는 요소를 존재하는 것처럼 부여
```

### CSS 가상 클래스 종류
```
 - :hover : 마우스 롤오버시
 - :active : 마우스 클릭시
 - :focus : input태그 등이 포커스 되었을 시
 - :first-of-type : 모든 자식 요소 중에서 첫 번째에 등장하는 특정 요소를 선택
 - :last-of-type : 모든 작식 요소 중에서 마지막으로 등장하는 특정 요소를 선택
 - :first-child : 모든 자식 요소 중에서 첫 번째에 위치하는 자식을 선택
 - :last-child : 모든 자식 요소 중에서 마지막에 위치하는 자식을 선택
```

### CSS 가상 요소 종류
```
 - ::before : 요소의 컨텐츠 시작부분에 생성된 컨텐츠를 추가
 - ::after : 요소의 컨텐츠 끝 부분에 생성된 컨텐츠를 추가
 - ::selection : 마우스 드래그로 선택한 텍스트 콘테츠 영역을 선택
 - ::marker: 목록 아이텡 앞에 붙는 마커 선택
 - ::first-letter : 현재 웹브라우저에 보이는 상태를 기준으로 요소의 
                    텍스트 콘테츠 첫 글자 선택
 - ::first-line : 현재 웹브라우저에 보이는 상태를 기준으로 요소의
                  첫 줄 내용을 선택
```

### CSS Float과 Clear
```
 - float : 텍스트 및 인라인 요소가 주위를 둘러싸게 할 수 있음
 - clear : float의 영향을 받지 않도록 할 수 있음
```

### CSS Box Model
```
 - content : 텍스트와 이미지가 나타나는 상자 내용
 - padding : 콘텐츠 주변 영역을 지움
 - border : 패딩과 콘텐츠를 둘러싸는 테두리
 - margin : 테두리 밖의 영역 
```

### CSS 이미지 object-fit 종류
```
 - fill : 기본값, 주어진 치수 채우도록 조정, [늘어나거나 찌끄러짐]
 - contain : 이미지 종횡비 유지, 주어진 치수에 맞게 크기 조정
 - cover : 이미지 종횡비 유지, 주어진 치수 채움, [이미지 잘림]
 - none : 이미지 크기 조정 x
 - scale-down : 이미지가 none or 포함의 가장 작은 버전으로 축소
```

### CSS Transform
```
 - transition : 시간을 흐름의 주는 속성
 - animation : 하나의 줄거리를 구성하여 줄거리 내에서 세부 움직임을 시간흐름 단위로
               제어하여 요소의 움직임을 표현
 - transform : 회전, 크기 조절, 기울이기, 이동 효과 부여
```

### CSS background-clip
```
 - boredr-box : 테두리 영역과 그 안쪽 영역을 채움
 - padding-box : 안쪽 여백 영역과 그 안쪽 영역을 채움
 - content-box : 내용영역과 그 안쪽 영역을 채움
 - initial : 기본값 설정
 - inherit : 부모 요소의 속성 값을 상속받음
```

### CSS Flexbox
```
 - 요소를 효율적이고 동적으로 배열할 수 있는 레이아웃 모델

 * Flex Container : Flexbox의 이 구성 요소는 표시를 flex or inline-flex로 
                    설정하여 상위 요소의 속성을 정의
 * Flex Items : Flex Container의 직계자식
```

### CSS Flexbox Properties
```
 - Flex Container Properties 종류
    * flex-direction
    * flex-wrap
    * flex-flow
    * justify-content
    * align-items
    * align-content

 - Flex Items Properties 종류
    * order
    * flex-grow
    * flex-shrink
    * flex-basis
    * align-self
    * flex : flex-grow, flex-shrink, flex-basis가 결합된 약어
```
