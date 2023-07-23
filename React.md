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
   </br>
   </br>

### **컴포넌트의 Lifecycle**

```JSX
import { useEffect, useState } from 'react';

function App() {
  let [btn, setBtn] = useState(true);

  useEffect(() => {
    let timeout = setTimeout(() => {
      setSwitch(false);
    }, 2000);

    return()=>{
      // clean up function 이라는 별명을 가졌고,
      // 기존에 있던 코드를 다 삭제해서 버그가 일어나지 않게 방지해주는 역할을 한다.

      // 1. 기존에 있던 timeout이라는 타이머를 제거해주세요~
      cleanTimeout(timeout);
    }
  });

  return(
    <div>
      {
        btn === true
        ? <button type="button">
            switch가 true일 때만 태그가 보이도록 하기.
          </button>
        : null
      }
    </div>
  );
}
```

- 컴포넌트의 **Lifecycle에는 3가지가** 있다.

1. mount(페이지에 장착 된 경우)
2. update(업데이트 된 경우)
3. unomount(필요없어서 삭제 된 경우)
   </br></br>

- **useEffect()** 를 사용할 때

1. 페이지가 **재랜더링** 될 때마다 코드를 실행하고 싶을 때
   </br></br>

- **useEffect() 안에 쓸 코드 종류**

1. 어려운 연산 (중첩 for문 등..)
2. 서버에서 데이터 가져오는 작업
3. 타이머 장착하는 거(setTimeout 등..)
   </br></br>

- **useEffect() 종류 3가지**

1. `useEffect(() => {})` 재랜더링 될 때마다 실행
2. `useEffect(() => {}, [])` mount시 1회 코드를 실행하고 싶을 때
3. `useEffect(() => { return()=>{} }, [])` unmount시 1회 코드를 실행하고 싶을 때
4. `useEffect(() => {}, [change])` change 라는 state가 변경될 때마다 코드를 실행하고 싶을 때
   </br>
   </br>

### **AJAX로 서버에서 데이터 받아오기**

- 서버에서 데이터를 가져오려면 **단계**가 있다. </br>
  ex) 네이버에서 웹툰을 불러와보자.

1. 어떤 방법으로 데이터를 보낼 것인지 **(GET / POST)** </br>
   ex) comic.naver.com (GET 요청)
2. 어떤 자료를 가져와달라고 할 것인지 **(URL 형식)** </br>
   ex) 서버 개발자에게 물어보면 된다.
   </br></br>

- 이제 진짜 **ajax 사용하기**

1. `npm install axios` 를 터미널에 입력한다.
2. `import axios from 'axios';` 라고 코드를 입력한다.
3. `axios.get()`은 **GET 요청**으로 데이터를 보내는 것을 의미한다.
4. () 안에는 서버 개발자가 만든 **URL**을 입력하면 된다.
5. 최종 코드는 `axios.get('url').then()`이다.
   </br></br>

```JSX
import axios from 'axios';

function Detail() {

  // then 안에 들어있는 데이터에는 내가 찾아온 데이터가 들어있다.
  return(
    <button type="button" onClick={() => {
      axios.get('https://codingapple1.github.io/shop/data2.json')
      .then((result) => {
        console.log(result);
      })
      .catch(() => {
        console.log('실패했을 때 실행될 함수');
      })
      }}
    >
      더보기
    </button>
  );
}
```

- 이번엔 **ajax 활용하기** </br>
  `ajax로 데이터를 받아와서 버튼을 누르면 화면에 보이는 실습하기`

```JSX
import axios from 'axios';
import {useState} from 'react';

function Detail() {

  //버튼을 클릭했을 때만 보여주기 위해서 onClick state를 만들었다.
  let [onClick, setOnClick] = useState(true);

  let [products, setProducts] = useState([]);

  return(
    <div>
      <button type="button" onClick={() => {
        axios.get('https://codingapple1.github.io/shop/data2.json')
        .then((result) => {
          if(onClick) {
            setOnClick(false);
            setProducts([]);
          } else {
            setOnClick(true);
            setProduct([...result.data]);
          }
        })
        .catch(() => {
          alert('데이터가 없습니다.');
        })
      }}>
        더보기
      </button>

      <div>
      {
        products.map((item) => {
          return(
            <article>
              <h1>{item.title}</h1>
              <span>{item.price}</span>
              <p>{item.content}</p>
            </article>
          );
        })
      }
      </div>
    </div>
  );
}
```

</br>
</br>

### **IF 조건문으로 탭 만들기**

```JSX
import { useState } from 'react';

function App() {
  let [tab, setTab] = useState(0);

  return(
    <div>
      <div>
        <button type="button" onClick={() => { setTab(0); }}>
          탭1
        </button>
        <button type="button" onClick={() => { setTab(1); }}>
          탭2
        </button>
        <button type="button" onClick={() => { setTab(2); }}>
          탭3
        </button>
      </div>

      {/
        변경된 tab 값을 전달해서 조건문에 맞는 컴포넌트가 보여지게 된다.
      /}
      <TabContent tab={tab} />
    </div>
  );
}

function TabContent(props) {
  let tab = props.tab;

  if(tab === 0) {
    return(
      <div>
        <span>탭1 버튼을 눌렀을 때 나오는 창입니다.</span>
      </div>
    );
  }
  if(tab === 1) {
    return(
      <div>
        <span>탭2 버튼을 눌렀을 때 나오는 창입니다.</span>
      </div>
    );
  }
  if(tab === 2) {
    return(
      <div>
        <span>탭3 버튼을 눌렀을 때 나오는 창입니다.</span>
      </div>
    );
  }
}
```

- **조건문 컴포넌트 사용하는 이유**</br>
  HTML 안에 `삼항 연산자`를 사용할 수 있지만 {} 안에 1개만 사용할 수 있어 코드가 복잡해진다.</br>
  따라서 `조건문 컴포넌트`를 사용하면 코드의 가독성이 좋아진다.
  </br></br>

```JSX
//조건문 컴포넌트 내용을 이렇게 바꿔쓸 수도 있다.

function TabContent({tab}) {

  /*
    tab이 0이면 내용1이 출력된다.
    이렇게 조건문을 사용하지 않아도 된다.
  */
  return(
    [<div>내용1</div>, <div>내용2</div>, <div>내용3</div>][tab]
  );
}
```

- `props.tab` 이렇게 사용하고싶지 않을 때 위 코드처럼 변수를 {}로 감싸면 `props.`을 붙이지 않고 변수명만 쓸 수 있다.</br>
  (여러 개면 `{변수1, 변수2, ...}` 이렇게 작성하면 된다.)
  </br>
  </br>

### **Redux Toolkit 사용하기**

```jsx
import { configureStore, createSlice } from "@reduxjs/toolkit";

//useState와 비슷한 역할
let user = createSlice({
  name: "user",
  initialState: "Kim"

  reducers: {
    // 인자도 넣을 수 있다.
    state수정함수(state){
      return '변경하고 싶은 값' + state
    }

    changeName(state){
      return 'Lee' + state
    }
  }
});

export let { changeName } = user.actions;

let stock = createSlice({
  name: "stock",
  initialState: [10, 11, 12]
});

let login = createSlice({
  name: 'login',
  initialState: {email: '', pass: '', nickname: ''},

  //input은 changeLogin(인자)에 들어오는 값을 의미한다.
  changeLogin(state, input) {
    return state.nickname = input;
  }
});

export { changeLogin } = login.actions;

export default configureStore({
  reducer: {
    user: user.reducer,
    stock: stock.reducer,
  },
});
```

- **Redux Toolkit 장점**</br>
  컴포넌트 간에 state 공유가 편해집니다.

- **Redux Toolkit 사용방법**

1. 터미널에서 `npm install @reduxjs/toolkit react-redux` 를 입력한다.
2. state를 보관할 파일을 생성한다.
3. **index.js에서** <Provider store={store}>로 요소들을 다 깜싼다.
   (store={store}는 내가 생성한 redux 파일 명을 쓰면 된다!)

---

4. 위에 처럼 redux 페이지를 저렇게 작성한다.
5. **createSlice는** state를 생성하고 수정하는(reducers) 함수도 생성한다, **reducer에는** state를 등록해야 하는 곳이다. (reducer에 등록해야 다른 컴포넌트에서 사용이 가능하다.)
6. reducers에 생성한 함수는 반드시 `export` 해야 한다.
   </br>
   </br>

### **Redux 생성한 state 사용하기**

```jsx
// detail.js 코드이다.
import { useDispatch, useSelector } from "react-redux";
import { changeName } from './../store.js';

function Detail() {
  // 저장된 state가 담겨져있다.
  let state = useSelector((state) => {
    return state;
  });

  // user만 가져올 수 있다.
  let user = useSelector((state) => {
    return state.user;
  });

  // redux 파일에 요청을 보내는 함수이다.
  let dispatch = useDispatch();

  return {
    <div>
      <span>{user}</span>
      <button onClick={() => {
        dispatch(changeName())
      }}>
      </button>
      <h1>{state.login}</h1>
      <input type="text" onChange={() => {dispatch(changeLogin(e.target.value))} } />
    </div>
  };
}
```

- **redux 다른 컴포넌트에서 사용하기**

1. useSelector를 사용해서 state를 가져온다.
2. 함수를 가져올 때는 import하고, `dispatch 변수를 생성`해야 한다.

- **useSelector 특징**

1. 반환된 값이 마지막 값과 달라지지 않으면 재렌더링 하지 않는다.
   </br>
   </br>

### React 배포할 때 빈 페이지가 나올 때 해결하는 법

```js
// 파일명: index.js
import { BrowserRouter } from "react-router-dom";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <BrowserRouter basename={process.env.PUBLIC_URL}>
    <App />
  </BrowserRouter>
);
```

- **BrowserRouter에 basename props 넣기**

1. `process.env.PUBLIC_URL`의 의미는 .env 파일에서 PUBLIC_URL의 값을 가져온다는 것이다.
2. basename이 root가 되어서 정상적이게 페이지가 동작한다.
   </br>
   </br>

### React 배포할 때 이미지가 안 보일 때 해결하는 법

- **src에 /리파지토리명/이미지경로 를 사용하기**

1. `내아이디.github.io/리포지토리명/`으로 배포를 한 경우 이미지 경로 앞에 무조건 `/리파지토리명`을 써줘야 한다.
   </br>
   </br>

### React 배포할 때 react to load resource: the server responded with a status of 404 () 오류 해결

```json
// 파일 이름: package.json
{
  "homepage": "https://robbeca-code.github.io/cook",
  "proxy": "https://robbeca-code.github.io/cook",
  "name": "cook",
  ...
}
```

- **proxy에 배포한 경로를 적어준다.**

1. 프론트와 백엔드가 서로 연동이 안되어 있을 때 발생하는 오류이다.
2. 해결하기 위해 `"proxy": "배포한_경로"`를 적어줘서 서로 연동되게 만든다.
   </br>
   </br>

### DOM property `frameborder`. Did you mean `frameBorder`? 오류 해결

```html
<!-- 오류가 발생한 코드 -->
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/jC41T25dImI"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
></iframe>

<!-- 오류를 해결한 코드 -->
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/jC41T25dImI"
  title="YouTube video player"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen
></iframe>
```

- **frameborder를 frameBorder로 변경한다.**

1. JSX에선 frameBorder로 사용해야 한다.
2. 비슷한 예로, JSX에선 태그에 클래스명을 사용할 때 `class`가 아닌 `className`을 사용해야 하는 것이 있다.
   </br>
   </br>

### Failed to get remote.origin.url 오류 해결

```
Failed to get remote.origin.url (task must either be run in a git repository with a configured origin remote or must be configured with the "repo" option).
```

- **git remote origin을 변경해줘야 한다.**

1. git remote -v를 했을 때 origin의 경로가 잘못되어있다면 맞게 고쳐야 한다.
2. origin으로 잘 되어있고 경로가 잘못된 것이 아니라면 git의 경로 중 `http와 SSH 중 처음 것과 다른 걸로` 변경해줘야 한다.
