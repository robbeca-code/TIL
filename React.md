# [React](README.md)

### **React 장점 2가지**

1. Single Page Application 개발할 때 사용한다. (새로고침 없이 부드럽게 앱처럼 동작할 수 있다.)

2. html을 함수로 담아서 쓰기 때문에 재사용이 편리하다.
   </br>
   </br>

### **JSX란**

- 자바스립트와 HTML 문법을 같이 쓸 수 있는 문법이다.
  </br>
  </br>

### **태그에 클래스를 줄 때 className이라고 써야하는 이유**

- 자바스크립트에서 class라는 개념이 따로 있어서 똑같이 class라고 주면 겹치기 때문이다.
  </br>
  </br>

### **데이터바인딩**

```JSX
let post = '우동 맛집';

<div className={post}>{post}</div>
```

- JSX 문법에서 변수를 쓸 때 {}로 묶어주고 HTMl에 변수를 넣어주는 것을 데이터바인딩이라고 한다.
  </br>
  </br>

### **태그에 style 속성 주기**

```JSX
<div style={{color: 'red', fontSize: '16px'}}>블로그</div>
```

- style을 줄 땐, object 형식으로 줘야 한다. </br>
  font-size를 fontSize로 표현하는 이유는 자바스크립트에선 -는 빼기 연산자이기 때문이다.
  </br>
  </br>

### **return 안에는 태그 1개로 묶어서 사용한다.**

```JSX
//function은 생략했다.

return (
  <div className="App">
    <nav className="black-nav">
      <h1>맛집 블로그</h1>
    </nav>
    <ol className="blog-list">
      <li>
        <h3>글제목</h3>
        <p>생성 날짜</p>
      </li>
    </ol>
  </div>
  );
```

- return 안에는 태그 1개로 시작해서 1개로 끝나야 한다.
  </br>
  </br>

### **자료를 잠깐 저장할 때 state 사용하기**

```JSX
import { useState } from 'react';

function App() {
  let [a, b] = useState('잠깐 저장할 자료');

  return (
    <div className="App">
      <h4>{ a }</h4>
    </div>
  );
}

```

- **a**는 useState의 저장한 자료를 담고 있고,</br>
  **b**는 useState를 변경해주는 인자이다.
  </br>
  </br>

### **useState는 언제 사용해야 하는가**

```JSX
import { useState } from 'react';

function App() {
  let [a, b] = useState('잠깐 저장할 자료');

  // return 안에 있는 html 전체가 재렌더링 된다.
  return (
    <div className="App">
      <h4>{ a }</h4>
      <div></div>
      <div></div>
      <div></div>
    </div>
  );
}

```

- 변수의 값이 달라지면 html에 바로 반영되지 않는다. 그러나 useState를 사용했을 때 값이 달라지면 html은 자동으로 재렌더링이 된다.
  </br></br>
  즉, 자주 변경될 것 같은 html은 state로 작성한다.
  </br>
  </br>

### **버튼 누를 때 숫자 1씩 증가시키기**

```JSX
import { useState } from 'react';

function App() {
  let [count, setCount] = useState(0);

  return (
    <div className="App">
      <button type="button" className="like-btn" onClick={()=>{setCount(count + 1)}}>
        👍
      </button>
      <span className="like-count" onClick={}>
        {likeCount)}
      </span>
    </div>
  );
}

```

- onClick={} 안에는 항상 함수명이나 함수 문법을 넣어줘야 한다.</br>
  state의 값을 변경하고 싶을 땐 두 번째 인자를 사용한다. 두 번째 인자는 함수라서 **함수명(변경할 값)** 이렇게 사용하면 state 값이 변경된다.
  </br>
  </br>

### **state가 변경이 될 때와 안될 때**

```JSX
import { useState } from 'react';

function App() {
  let [title, setTitle] = useState(['여자 코트 추천', '여자 가방 추천']);

  return (
    <div className="App">
      <button type="button" className="like-btn" onClick={()=>{
          // 변경이 안되는 틀린 코드
          title[0] = '남자 코트 추천';
          setTitle(title);


          // 변경이 되는 옳은 코드
          let copyTitle = [...title];
          copyTitle[0] = '남자 코트 추천';
          setTitle(copyTitle);
        }}>
        제목 수정
      </button>
    </div>
  );
}
```

- state를 변경할 때는 **원본값의 내용이 변경**되는게 아니라, 아예 **다른 변수로 변경되어야** 원하는 값으로 변경된다.
  </br>
  </br>

### **컴포넌트 문법**

```JSX
import { useState } from 'react';

function App() {
  return (
    <div className="App">
      <Modal></Modal>
    </div>
  );
}

function Modal() {
  return(
    <aside className="modal">
      <h3>제목</h3>
      <span>날짜</span>
      <p>상세내용</p>
    </aside>
  );
}
```

- **만드는 방법**

1. function을 만들고 함수명 시작은 대문자로 한다.
2. return() 안에 html을 담는다.
3. <함수명></함수명> 사용한다.
   </br>

- **왜 사용하는가?**</br>
  HTML에 div가 너무 많아지면 각각이 무슨 역할을 하는지 알아보기 힘들 때가 있다.</br>
  그래서 컴포넌트를 사용하면 해당 태그가 무슨 역할을 하는지 바로 알 수 있다.

- **언제 사용하면 좋은가**

1. 반복적인 html을 축약할 때
2. 페이지 전환할 때 컴포넌트로 사용하기
3. 자주 변경되는 html UI
   </br>
   </br>

### **이미지 넣기**

```JSX
import img from './assets/event.png';

function App() {
  return (
    <div className="App">
      <img src={img} alt="The event image"/>
    </div>
  );
}
```

- **import <사용할 이름> from <이미지 파일 경로>;** 이렇게 사용하면 된다.
  </br>
  </br>

### **조건식 사용하기**

```JSX

function App() {
  let [modal, setModal] = useState(false);

  return (
    <div className="App">
      {
        // modal이 true면 <Modal/>을 보여주고 아니면 null 반환.
        // null은 비어있는 html용으로 자주 사용한다.
        modal === true ? <Modal/> : null
      }
    </div>
  );
}

function Modal() {
  return(
    <aside className="modal">
      <h3>제목</h3>
      <span>날짜</span>
      <p>상세내용</p>
    </aside>
  );
}
```

- JSX는 HTML을 작성하는 문법으로 자바스크립트 문법인 if문을 사용할 수 없어서 **삼항 연산자**를 대신 {} 안에 사용한다.
  </br>
  </br>

### **동적인 UI 만들기**

```JSX

function App() {
  let [modal, setModal] = useState(false);

  return (
    <div className="App">
      <button type="button" onClick={() => {
        if(modal) {
          setModal(false);
        } else {
          setModal(true);
        }
      }}>
      {
        modal === true ? <Modal/> : null
      }
    </div>
  );
}

function Modal() {
  return(
    <aside className="modal">
      <h3>제목</h3>
      <span>날짜</span>
      <p>상세내용</p>
    </aside>
  );
}
```

- 조건문을 사용해서 동적인 UI를 만들 수 있다.
  </br>
  </br>

### **부모 state를 자식에게 전송하기**

```JSX

function App() {
  let [title, setTitle] = useState(['가방','양말','신발']);
  let [modal, setModal] = useState(false);

  return (
    <div className="App">
      <button type="button" onClick={() => {
        if(modal) {
          setModal(false);
        } else {
          setModal(true);
        }
      }}>
      {
                              //작명 = {state이름}
        modal === true ? <Modal title={title}/> : null
      }
    </div>
  );
}

function Modal(props) {
  return(
    <aside className="modal">
      {/* props.작명 */}
      <h3>props.title</h3>
      <span>날짜</span>
      <p>상세내용</p>
    </aside>
  );
}
```

- 다른 컴포넌트에 있는 state를 사용하고 싶을 때, 그게 부모라면 props로 받아올 수 있다.</br>
  **무조건 부모에서 자식한테만 state를 전송할 수 있다.**
  </br>
  </br>

### **class 문법**

```JSX
//부모 안에 작성했을 때 이렇게 props를 받아올 수 있다.
<App title={title} />


class App extends React.Component {
  constructor(props) {
    // 여기 안에 state를 작성하거나
    // 부모로부터 props를 받아올 수 있다.
    this.state = {
      name: 'Banana',
      color: 'Yellow'
    };
    super(props);
  }
  render() {
    return(
      <div>
        <span>여기에 html을 작성한다.</span>
        <span>{this.state.name}</span>
        <span>{this.props.title}</span>
      </div>
    );
  }
}
```

- class 문법은 예전에 많이 사용했던 문법이다. 과거에 썼던 리액트 프로젝트들엔 이런 문법이 많기 때문에 많이 봐두는게 좋다.</br>
  class 문법에서 꼭 들어가야 할 것들은 **constructor(), super(), render()**이다.</br>
  </br>

### **public 폴더에 이미지 넣기**

```JSX
function App() {
  return (
    <div className="App">
      <img
        src={process.env.PUBLIC_URL + '/public-assets/logo.png'}
        alt="The logo image"/>
    </div>
  );
}
```

- **public에 이미지 폴더 넣을 때**는 대부분 이미지 개수가 너무 많을 때 사용한다.</br>
  process.env.PUBLIC_URL 을 권장하지만 이거 없이 사용해도 이미지는 나온다.
  </br>
