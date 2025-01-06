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
 - 컴포넌트 내부에서 코드를 작성한다 << 컴포넌트(재사용이 가능한 독립 모듈)
    

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


## 조건부 렌더링
- javascript에서는 null, false, undefined를 렌더링 하면 아무것도 나타나지 않는다.
- 삼항연산자를 이용해 조건부 렌더링 가능
        

        <div style={{color}}>
            { isSpecial ? <b>*</b> : null}
            안녕하세요 {name}
        </div>

- &&를 사용할 경우
    

    &&를 사용하면 첫번째로 나오는 false 값을 반환하며, 없다면 마지막 값을 반환

        <div style={{color}}>
            { isSpecial && <b>*</b>}
            안녕하세요 {name}
        </div>

## useState
### 화살표 함수
- 형태
  

  React에서 이벤트 설정을 주로 on이벤트 이름 = "{싱행하고 싶은 함수}" 형태로 작성

        const funcName () => {
            //body
        }

### state 선언 방식

        
        const [number, setNumber] = useState(0);
            return {
                <div>{number}</div>
            }

## Input
- input의 onChange를 사용하면 이벤트 객체 e 파라미터로 받아올 수 있다.
- 이 객체의 e.target은 이벤트가 발생한 DOM을 가리킨다.
- e.target.value를 조회하면 현재 input의 value값을 알 수 있다.

        import React, { useState } from 'react';

        function InputSample() {
            const [text, setText] = useState('');

            const onChange = (e) => {
                setText(e.target.value);
            };

            const onReset = () => {
                setText('');
            };

            return (
                <div>
                <input onChange={onChange} value={text}  />
                <button onClick={onReset}>초기화</button>
                <div>
                    <b>값: {text}</b>
                </div>
                </div>
            );
        }

        export default InputSample;