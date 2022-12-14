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
  </br>

### **다른 js 파일에 있는 데이터를 사용하고 싶을 때**

```JSX
/*     data1.js     */
let a = 10;

export default a;
// export default 변수명; 이렇게 하면 다른 파일에서 데이터를 가져가서 사용할 수 있다.


/*     data2.js     */
let num1 = 10;
let num2 = 20;

export {num1, num2};


/*     App.js     */
import data from './data1';
import {num1, num2} from './data2';
// import 작명 from '경로';
// import {여러개 할 때는 변수명 그대로 사용해야 한다} from '경로';
```

- **export를 사용하는 경우**

1. 변수가 너무 길 때
2. 함수를 나누어서 사용하고 싶을 때
   </br>
   </br>

### **react-router-dom 라이브러리 사용하기**

```JSX
import {Routes, Route, Link} from 'react-router-dom';

function App() {
  return(
    <Link to="/">홈</Link>
    <Link to="/detail">상세페이지</Link>

    <Routes>
      <Route path="/" element={<div>메인 페이지</div>} />
      <Route path="/detail" element={<div>상세 페이지</div>} />
    </Routes>

    /*
      Route를 하나의 링크라고 생각하면 된다.
      path는 경로명으로 이것을 URL 창에 입력하면 element가 브라우저에 보여지게 된다.
      **이때 path="/"는 메인 페이지를 의미한다.**
    */
  );
}
```

- **라우터를 사용하는 방법**

1. 터미널에 `npm install react-router-dom@6`을 입력해서 다운받는다. (@6은 6버전을 의미한다.)
2. **index.js** 파일에서 import {BrowserRouter} from "react-router-dom"; 을 입력한 후,</br>
   `<React.StrictMode>` 안에 있던 것들을 `<BrowserRouter>`으로 묶어준다.
3. 라우터를 사용할 파일에는 import {Routes, Route, Link} from 'react-router-dom';을 입력하고 </br>
   위의 코드처럼 사용한다.
   </br>
   </br>

### **라우터에서 가장 많이 쓰이는 것들**

```JSX
// 1. useNavagate 사용하기
import { Link, useNavigate } from 'react-router-dom';

function App() {
  return(
    let navigate = useNavigate();

    <Link to="/detail">Detail</Link>
    <button type="button" onClick={useNavigate('/detail')}>Detail</button>
    /*
      Link 태그를 사용하면 html에 <a> 로 보여지게 된다.
      만약 <a>태그 말고 다른 태그로 사용하고 싶은데 페이지 이동을 하고 싶을 때,
      useNavigate()를 사용하면 된다.
    */
  );
}
```

- **useNavigate()** 는 페이지 이동을 도와주는 훅이다.</br>
  () 안에는 경로 뿐만 아니라 다른 값도 넣을 수 있다.</br>
  **useNavigate(-1)** 은 뒤로 1번 이동을 의미하고 **useNavigate(1)**은 앞으로 1번 이동을 의미한다.
  </br>
  </br>

```JSX
// 2. 404 페이지 만들기
import { Routes, Route, Link, useNavigate } from 'react-router-dom';

function App() {
  return(
    <Routes>
      <Route path="/detail" element={<div>상세 페이지 입니다.</div>} />
      <Route path="*" element={<div>없는 페이지 입니다.</div>} />
    </Routes>
    /*
      /detail 을 제외한 다른 경로들은 없는 경로이기 때문에
      path="*"를 줘서 /detail 을 제외한 모든 경로는 없는 페이지(404 페이지)가 보이도록 할 수 있다.
    */
  );
}
```

</br>
</br>

```JSX
// 3. Nested Routes과 Outlet 사용하기
import { Routes, Route, Link, useNavigate } from 'react-router-dom';

function App() {
  return(
    <Routes>
      <Route path="/detail" element={<Detail />} />
      <Route path="/detail/review" element={<div>상세 페이지의 리뷰 페이지 입니다.</div>} />
      <Route path="/detail/ask" element={<div>상세 페이지의 질문 페이지 입니다.</div>} />


      <Route path="/detail" element={<Detail />}>
        <Route path="/review" element={<div>상세 페이지의 리뷰 페이지 입니다.</div>} />
        <Route path="/ask" element={<div>상세 페이지의 질문 페이지 입니다.</div>} />
      </Route>
    </Routes>
    /*
      하위 메뉴에서 또 다른 하위 메뉴로 이동하고 싶을 땐, <Route> 안에 <Route>를 작성해주면 된다.
    */
  );
}

function Detail() {
  return(
    <div>상세 페이지 입니다.</div>
    <Outlet></Outlet>
    // 이 부분에 하위 메뉴가 위치해서 보여지게 된다.
  );
}
```

- **Nested Route의 장점**

1. 하위 메뉴와 그것의 하위 메뉴 둘 다 브라우저에서 보여줄 수 있다. (이때 사용하는게 Outlet 이다.)
2. 코드 가독성이 좋아진다.

- **Nested Route를 사용하는 경우**

1. 여러 페이지를 이동할 때
2. 여러 유사한 페이지가 필요할 때(박스 1개만 바뀌면 되거나 글자 몇 개만 바뀌면 될 때)
   </br>
   </br>

### **:URL 파라미터로 페이지 여러 개 만들기**

```JSX
function App() {
  return(
    /*
      :URL은 상품의 상세 페이지를 만들 때 자주 사용하는 것이다.
      그래서 컴포넌트에 props만 다르게 주고 Page를 만들면 된다.
    */
    <Routes>
      <Route path="/detail/:id" element={<Shoes data1={data1} />}/>
      <Route path="/detail/:id" element={<Shoes data2={data2} />}/>
      <Route path="/detail/:id" element={<Shoes data3={data3} />}/>
      <Route path="/detail/:id" element={<Shoes data4={data4} />}/>
      <Route path="/detail/:id" element={<Shoes data5={data5} />}/>
    </Routes>
  );
}
```

- **:URL 파라미터를 사용하는 경우**

1. 한 페이지에서 내용만 달라지고 비슷한 의미를 전달하는 페이지가 여러 개 일때
2. 페이지가 너무 많을 때
   </br></br>

- **어떻게 작동하는가?**

1. /detail/[ 아무거나 ] URL에는 이렇게 ([]는 자리를 표시한 것 뿐이다.) [] 자리에 아무 값이나 오게 된다.</br>
   그래서 굳이 /detail/1 /detail/2 할 필요없이 /detail/:id 를 하면 편리하게 여러 개의 페이지를 만들 수 있다.
   </br>
   </br>

### **useParams()로 사용자가 입력한 URL 값 가져오기**

```JSX
import { useParams } from 'react-router-dom';

function User(props) {
  let {id} = useParams();

  <div>
    <header>
      <h1>{props.title[id]}</h1>
    </header>
    <div>
      <span>{props.description[id]}</span>
      <span>{props.price[id]}</span>
    </div>
  </div>
}
```

- **useParams()를 사용하면** 상세 페이지를 만들 때, URL에 입력된 값에 맞게 내용을 보여줄 수 있게 된다.
  </br>
  </br>

### **styled-components 사용하기**

```JSX
import styled from 'styled-components';

let YellowBtn = styled.button`
  background : yellow;
  color: black;
  padding: 10px;
`;

// 1. 비슷한 스타일은 props를 사용한다.
// 2. 조건문도 사용할 수 있다.
let ColorBtn = styled.button`
  background: ${props => props.bg};
  color: ${props => props.bg=='blue' ? 'white' : 'black'};
  padding: 10px
`;

let Box = styled.div`
  background: grey;
  padding: 20px;
`;

function App() {
  return(
    <div>
      <YellowBtn>노랑색 버튼</YellowBtn>

      <ColorBtn bg="blue">파랑색 버튼</ColorBtn>
      <ColorBtn bg="orange">주황색 버튼</ColorBtn>

      <div>검정색 바탕 박스</div>
    </div>

  );
}
```

- **styled-components 사용방법**

1. 터미널에 `npm install styled-components` 를 입력한다.
2. 위 코드처럼 작성하면 된다.
   </br>
   </br>

- **styled-components의 장점**

1. CSS 파일을 생성하지 않아도 된다.
2. 스타일이 다른 js파일과 충돌되지 않는다.
3. `<style>` 태그로 만들어져서 페이지 로딩 시간이 단축된다.
   </br>
   </br>

- **styled-components의 단점**

1. JS 파일이 매우 복잡해진다.
2. 협업할 때 이 코드를 보고 이해를 못하는 사람이 있을 수 있다.
