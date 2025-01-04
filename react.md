# React 정리

## JSX란 ?
 - 리액트 컴포넌트에서 xml 형식의 값을 반환하는 것

## JSX의 기본 규칙
 - 태그는 꼭 닫기
  
   두 개 이상의 태그는 무조건 하나의 태그로 감싸기    
 
 - JSX 내부에 자바스크립트 변수 
  
   {} 으로 감싸기

 - JSX 에서 style 과 CSS class

    인라인 스타일은  객체 형태로 작성 & camelCase 형태로 네이밍 class는 className= 으로 설정

 - JSX 내부 주석

    {/**/}, 열리는 태그 내부는 // 가능
  
## props란 ?
### 사용법
 - 컴포넌트 내부에서 코드를 작성한다 << 컴포넌트 이해 필요
    

        <Hello name="아무거나">    

- 받는쪽은 props 라는 예약어를 통해 받는다.
            

        function Hello(props) {
            return <div>{props.name}</div>
        }
    
### 비구조화할당
 - 컴포넌트의 파라미터에서 {}안에 받는 내용을 미리 표기한다.
  

        function Hello({name}) {
            return <div> {name} </div>
        }

### defaultProps
        function Hello({name, age}) {
            return <div> {name} </div>
        }

        Hello.defaultProps = {
            name='이름없음'
        }

### Props.children
- 컴포넌트 태그 사이에 값이 있을때 'children'이란 예약어를 사용한다.
