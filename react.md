# React 정리
### 목차


[1. JSX ](#jsx란-)


[2. JSX의 기본 규칙](#jsx의-기본-규칙)

[3. props](#props란-)

[4. 조건부 렌더링](#조건부-렌더링)

[5. useState](#usestate)

[6. input](#input)

[7. onChange](#onchange)

[8. onClick](#onclick)

[9. useRef](#useref)

[10. Map](#map을-이용한-렌더링)


## JSX
 - 리액트 컴포넌트에서 xml 형식의 값을 반환하는 것

## 기본 규칙
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

## onChange
- 변할때마다 실행
- 주로 input 태그의 이벤트 값을 받아와서 name과 value를 비구조화 할당을 통해 추출
        
        const onChange = (e) => {
            const {value, name} = e.target;
            setInputs({
                ...inputs,
                [name]: value
            });
        };
## onClick
- 클릭되면 실행된다

        <button onClick={onReset}>초기화</button>
### 정리
- 비구조화 할당: 객체를 추출하는 방법
- 구조분해 할당: 객체나 배열을 변수로 분해할 수 있게 해주는 특별한 문법

## useRef
- javasrcipt에서 특정 Dom을 선택하는 역할 ex) getElementByld, querySelector
- 특정 DOM에 접근할 때 사용
- 외부 라이브러리 사용할때 유용
- 원하는 위치에 ref={}의 형태로 작성
- 포커스를 잡으려면 nameInput.current.focus()형태로 작성

        const nameInput = useReft();

        const onClick = () => {
            nameInput.current.focus();
        }

        return( 
            <input ref={nameInput} />
            <button onClick={onClick}>클릭</button>
        )

## Map을 이용한 렌더링
- arr.map(i => )의 형태로 하위 컴포넌트에게 값을 전달해준다.
### Map에서 Key가 필요한 이유
- Map에 Key값이 없다면 중간의 값이 바뀌었을때 그 하위 값들이 전부 변한다. Key값을 사용한다면 Key를 이용해 중간의 값을 추가함