### CSS?
```
사용자에게 문서를 표시하는 방법을 지정하는 연어
```

### CSS 사용 방법 종류
```
 - 인라인 스타일 : HTML 안에서 Style속성을 이용하는 방법
 - 내부 스타일 시트 : <style>태그를 통해서 HTML 문서 내부에서 이용하는 방법
 - 외부 스타일 시트 : 별도 CSS 파일을 HTMl의 문서에 연결하는 방법

 * 우선순위 : 인라인 > 내부, 외부 > 웹 브라우저 기본
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
    * flex-direction : 정렬 방향 설정
    * flex-wrap : 줄바꿈 설정
    * flex-flow : flex-direction 및 flex-wrap 속성의 약어
    * justify-content : 주축을 따라 정렬 
    * align-items : 축의 수직 방향을 기준으로 정렬
    * align-content : align-items의 연장선, 2줄 이상부터 사용함

 - Flex Items Properties 종류
    * order : 플렉스 컨테이너 순서 제어
    * flex-grow : 플렉스 박스 아이템의 기본 너비를 자동으로 맞춰줌
    * flex-shrink : 플렉스 박스 아이템의 기본 너비 축소
    * flex-basis : flex 아이템의 기본 사이즈를 지정하는 속성
    * align-self : 개별 정렬
    * flex : flex-grow, flex-shrink, flex-basis가 결합된 약어
```

### CSS Position
```
 - static : 기본값, 다른 태그와의 관계에 의해 자동으로 배치되며 위치를 임의 설정 x
 - relative : 요소 자기 자신을 기준으로 배치 (원래 있던 위치를 기준)
 - absolute : 부모(조상)요소를 기준으로 배치, 부모요소에 static이 아닌 것이 있으면 
              그것을 기준 없다면 body를 기준으로 배치
 - fixed : 스크롤과 상관없이 항상 문서 최좌측 상단을 기준으로 좌표 고정 
           (스크롤 시 같이 내려감)
 - sticky : 스크롤 영역 기준으로 배치
```


### CSS Z-index
```
 - Z-index : 앞과 뒤에 나타나는 요소를 결정
 
 * z-index가 더 높은 요소는 z-index가 더 낮은 요소 앞에 나타남(음수 사용가능)
 * 기본 z-index는 0
 * 순서 값이 없을 경우 코드상 순서에 따라 쌓임
 * position: static 스타일을 가진 요소는 항상 뒤에 나타남 (z-index 효과 x)
 * z-index가 같거나 두 요소가 position:static이면 코드에서 나중에 작성된 요소가 앞
 * 부모에게 z-index값을 줄 경우 부모끼리 먼저 z-index순위를 정한 뒤 자식이 적용
   즉, 자식의 z-index값을 아무리 높여도 부모의 값이 낮으면 위로 올라올 수 없음
```

### CSS Media Query
```
 - 미디어 쿼리는 화면 해상도, 기기 방향 등의 조건으로 HTML에 적용하는 스타일을 전환할 수 있는
   CSS3의 속성 중 하나입니다. 반응형 웹 디자인에서는 미디어 쿼리를 사용해 적용하는 스타일을 기기
   마다(화면 크기마다)전환할 수 있습니다
 
 * 기본 문법
   @media [only 또는 not] [미디어 유형] [and 또는 ,] (조건문) {실행문}

 * [only 또는 not]
   - only : 미디어 쿼리를 지원하는 브라우저에서만 미디어 쿼리를 해석하게 해주는 키워드
   - not : not 다음에 따라오는 조건을 부정하는 키워드.
           ex) not print일 떄 print를 제외한 모든 미디어 유형에만 적용
 * [미디어 유형]
   - all : 모든 장치
   - print : 인쇄 장치
   - screen : 컴퓨터 화면 장치 또는 스마트 기기의 화면
   - tv : 영상과 음성이 동시에 출력되는 장치
   - projection : 프로젝터 장치
   - handheld : 손에 들고다니는 소형 장치
   - speech : 음성 출력 장치
   - aural : 음성 합성 장치 (TTS 장치)
   - embossed : 점자 인쇄 장치 (화면을 읽어 종이에 점자를 찍어내는 장치)
 * [and 또는 ,]
   - and : 앞뒤 조건이 모두 사실일 때 뒤에 따라오는 것을 해석하기
   - , : 앞뒤 조건 중 하나만 사실이라도 뒤에 따라오는 것을 해석하기
 * [min, max]
   - min : 크기가 작은 순서대로 작성
   - max : 크기가 큰 순서대로 작성
```

### CSS 적용 우선 순위
```
 1. !important를 붙인 속성
 2. HTML에서 style을 직접 지정한 속성
 3. #id로 지정한 속성
 4. 클래스, 가상클래스로 지정한 속성
```

### CSS -wepkit
```
 - webkit이란?
   * 웹 브라우저를 만드는 데 기반을 제공하는 오픈 소스 응용 프로그램 프레임워크 -wepkit-이라는 
     prefix는 표준화가 되지 않은 새로운 기능들의 속성일 경우 -wepkit- 이라는 prefix를 
     이용해서    
   * -webkit- : 구글, 사파리 브라우저에 적용
   * -moz- : 파이어폭스 브라우저에 적요
   * -ms- : 익스플로러에 적용
   * -o- : 오페라 브라우저에 적용
```

### CSS Grid
```
 - grid : Flexible Box는 단순한 1차원 레이아웃을 제공 (행, 열 하나씩)이에 비해 CSS Grid
          는 2차원의 레이아웃 시스템을 제공
 
 - grid 속성 종류
   * gap
   * grid-template-columns
   * grid-template-rows
   * repeat
   * 1fr
   * grid-column-start
   * grid-column-end
   * grid-row-start
   * grid-row-end
   * grid-template-areas : 그리드 레이아웃 내의 영역을 지정
```

### CSS ViewPort
```
 - width=deivce-width는 스크린의 width를 device의 width와 같게 설정
 - initial-scale=1.0 부분을 2.0으로 설정하면 화면 줌이 됨
```

### CSS Meta, Container Query
```
 - meta query는 일반적으로 viewport의 너비를 기준으로 적용
 - container query는 viewport대신 영역을 감싼 container를 기준으로 적용
```