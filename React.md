# [React](README.md)

#### **React 장점 2가지**

1. Single Page Application 개발할 때 사용한다. (새로고침 없이 부드럽게 앱처럼 동작할 수 있다.)

2. html을 함수로 담아서 쓰기 때문에 재사용이 편리하다.
   </br>
   </br>

#### **JSX란**

- 자바스립트와 HTML 문법을 같이 쓸 수 있는 문법이다.
  </br>
  </br>

#### **태그에 클래스를 줄 때 className이라고 써야하는 이유**

- 자바스크립트에서 class라는 개념이 따로 있어서 똑같이 class라고 주면 겹치기 때문이다.
  </br>
  </br>

#### **데이터바인딩**

```JSX
let post = '우동 맛집';

<div className={post}>{post}</div>
```

- JSX 문법에서 변수를 쓸 때 {}로 묶어주고 HTMl에 변수를 넣어주는 것을 데이터바인딩이라고 한다.
  </br>
  </br>

#### **태그에 style 속성 주기**

```JSX
<div style={{color: 'red', fontSize: '16px'}}>블로그</div>
```

- style을 줄 땐, object 형식으로 줘야 한다. </br>
  font-size를 fontSize로 표현하는 이유는 자바스크립트에선 -는 빼기 연산자이기 때문이다.
  </br>
  </br>

#### **태그에 style 속성 주기**

```JSX
<div style={{color: 'red', fontSize: '16px'}}>블로그</div>
```

- style을 줄 땐, object 형식으로 줘야 한다. </br>
  font-size를 fontSize로 표현하는 이유는 자바스크립트에선 -는 빼기 연산자이기 때문이다.
  </br>
  </br>

#### **return 안에는 태그 1개로 묶어서 사용한다.**

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

#### **자료를 잠깐 저장할 때 state 사용하기**

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

#### **useState는 언제 사용해야 하는가**

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
