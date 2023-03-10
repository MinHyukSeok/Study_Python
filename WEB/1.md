# HTML(Hyper Text Markup Language)
### Hyper Text
- 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트

### Markup Language
- 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어

> HTML : 웹 페이지를 구조화하기 위한 언어

## HTML 기본 구조
- html : 문서의 최상위 요소
- head : 문서의 메타 데이터 요소
  - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등
  - title : 브라우저 상단 타이틀
  - link : 외수 리소스 연결 요소
  - style : CSS 직접 작성

  - 일반적으로 브라우저에 나타나지 않는 내용
- boby : 문서 본문 요소
  - 실제 화면 구성과 관련된 내용


### 요소
- HTML 요소는 시작 태그와 종료 태그 그리고 태그 사이에 위치한 내용으로 구성
  - 태그는 컨텐츠를 감싸는 것으로 그 정보의 성격과 의미를 정의
- 내용이 없는 태그들
  - br, hr, input, link, meta
- 요소는 중첩될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화
  - 여는 태그와 닫는 태그의 쌍을 잘 확인해야함
    - 오류를 반환한는 것이 아닌 그냥 레이아웃이 꺠진 상태로 출력되기 때문에 디버깅이 힘들어 질 수 있음

### 속성
- 속성을 통해 태그의 부가적인 정보를 설정할 수 있음
- 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보를 제공
- 요소의 시작 태그에 작성하며 보통 이름과 값이 하나의 쌍으로 존재
- 태그와 상관없이 사용 가능한 속성(HTML Global Atttibute)들도 있음

#### HTML Global Atttibute
- 모든 HTML 요소가 공통으로 사용할 수 있는 대표적인 속성

### HTML 문서 구조화
- form
  - form은 사용자의 정보를 제출하기 위한 영역
- input
  - 다양한 타입을 가지는 입력 데이터 유형과 위젯이 제공됨

#### input label
- label을 클릭하여 input 자체의 초점을 맞추거나 활성화 시킬 수 있음
  - 사용자는 선택할 수 있는 영역이 늘어나 웹 / 모바일 환경에서 사용할 수 있음
  - label과 input 입력의 관계가 시각적 뿐만 아니라 화면 리더기에서도 label을 읽어 쉽게 내용을 확인 할 수 있도록 함
- input에 id속성을, label에는 for 속성을 활용하여 상호 연관을 시킴

# CSS(Cascading Style Sheets)
- 스타일을 지정하기 위한 언어
- 선택하고 스타일을 지정한다.

### CSS Selectors
- 기본 선택자
  - 전체 선택자(*), 요소 선택자
  - 클래스 선택자(.), 아이디 선택자(#), 속성 선택자
- 결합자
  - 자손 결합자, 자식 결합자

#### CSS 적용 우선순위
1. 중요도 - 사용시 주의
  - !important
  
2. 우선 순위
  - 인라인 > id > class, 속성 > 요소


### CSS 상속
- CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속한다.
  - 속성 중에는 상속이 되는 것과 되지 않는 것들이 있다.

#### 특정 값 상속 조정하기
``` HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .outer-box {
      width : 400px;
      height: 200px;
      border: 2px solid black;
    }
    .outer-box > div:first-child {
        color: red;
        text-align: center;
    }
		
    
    .inner-box {
      width : 200px;
      height: 100px;
      border: inherit;
    }

  </style>
</head>
<body>
  <div class="outer-box">
    <div>
      <span>첫 번째</span>
    </div>
    <div class="inner-box">
      <span>두 번째</span>
    </div>
  </div>
</body>
</html>

```

### Box model
- 모든 HTML 요소는 box 형태로 되어있음
- 하나의 박스는 네 부분으로 이루어짐
  - content
  - padding
  - border
  - margin

### box-sizing
- 기본적으로 모든 요소의 box-sizing은 content-box
  - padding을 제외한 순수 content 영역만을 box로 지정
- 다만, 우리가 일반적으로 영역을 볼 떄는 border까지의 너비를 보는 것을 원함
  - 그 경우 box-sizing을 border-box로 설정

### 크롬 개발자 도구
- 웹 브라우저 크롬에서 제공하는 개발과 관련된 다양한 기능을 제공
- 주요 기능
  - elements - DOM 탐색 및 CSS 확인 및 변경
    - Styles - 요소에 적용된 CSS 확인
    - Computed - 스타일이 계산된 최종 결과
    - Event Listeners - 해당 요소에 적용된 이벤트

## CSS Display
### 대표적으로 활용되는 display
- display: block
  - 줄 바꿈이 일어나는 요소(다른 elem를 밀어낸다)
  - 화면 크기 전체의 가로 폭을 차지한다.
  - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음.

- display: inline
  - 줄 바꿈이 일어나지 않는 행의 일부 요소
  - content를 마크업 하고 있는 만큼만 가로 폭을 차지한다.
  - width, height, margin-top, margin-bottom을 지정할 수 없다.
  - 상하 여백은 line-height로 지정한다.
  
- display: inline-block
  - block과 inline 레벨 요소의 특징을 모두 가짐
  - inline처럼 한 줄에 표시 가능하고, block처럼 width, height, margin 속성을 모두 저장할 수 있음
- display: none
  - 해당 요소를 화면에 표시하지 않고 공간조차 부여되지 않음


## CSS Position
- 문서 상에서 요소의 위치를 지정(어떤 기준으로 어디에 배치시킬지)
  - static : 모든 태그의 기본 값(기준 위치)
    - 일반적인 요소의 배치 순서에 따름(좌측 상단)
    - 부모 요소 내에서 배치될 때는 부모 요소의 위치를 기준으로 배치 됨

- 아래는 좌표 프로퍼티(top, bottom, left, right)를 사용하여 이동 가능
  - relative : 상대위치
    - 자기 자신의 static 위치를 기준으로 이동
    - 레이아웃에서 요소가 차지하는 공간은 static일 때와 같음
  - absolute : 절대 위치
    - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음
    - static이 아닌 가장 가까운 부모/조상 요소를 기준으로 이동(없는 경우 body)
  - fixed : 고정 위치
    - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간을 차지하지 않음
    - 부모 요소와 관계없이 viewport(내가 보는 화면)를 기준으로 이동
      - 스크롤 시에도 항상 같은 곳에 위치함 

  - sticky