# [JavaScript](README.md)

### **태그 안에 script 태그 사용하기**

```html
<!--#1. <head> 태그 안에 <script>를 넣었을 때 동작순서-->
<head>
  <title>head 태그 안에 script 넣기</title>
  <script src="main.js"></script>
</head>
<body></body>
```

1. html을 위에서부터 1줄씩 parsing 한다.
2. script 태그를 만나면 html의 parsing을 멈추고 다운받는다.
3. 다운을 다 받은 뒤 다시 parsing을 한다.

- **단점**
  - html의 규모가 클 수 록 속도가 오래 걸린다.
    </br></br>

```html
<!--#1. <body> 태그 안에 <script>를 넣었을 때 동작순서-->
<head>
  <title>body 태그 안에 script 넣기</title>
</head>
<body>
  <script src="main.js"></script>
</body>
```

1. html을 위에서부터 1줄씩 parsing 한다.
2. html을 다 parsing한 후
3. 페이지가 준비가 되면 script를 다운받는다.

- **단점**
  - script가 다운이 될 때까지 동작이 안된다.
    </br>
    </br>

### **JS async와 defer의 차이점**

```html
<!--#1. <head> 태그 안에 <script asyn>를 넣었을 때 동작순서-->

<head>
  <title>body 태그 안에 script 넣기</title>
  <script asyn src="main.js"></script>
  <!--asyn는 Boolean으로 선언만으로 true가 된다.-->
</head>
<body></body>
```

1. html은 위에서 아래로 1줄씩 parsing 하다가
2. asyn을 만나면 병렬로 script를 다운받는다.
3. 다운을 다 받으면 html의 parsing을 멈추고 script를 실행한다.
4. 실행이 끝나면 다시 html을 다운 받는다.

- **장점**
  - head에 넣어서 병렬적으로 동작해서 srcipt 다운받는 속도를 줄일 수 있다.
- **단점**
  - script를 실행할 때 html의 parsing을 멈추기 때문에 여전히 html parsing 속도는 느리다.
  - 먼저 다운 받아진 script를 먼저 실행한다.(`만약 순서에 의존하는 script라면 문제가 발생함.`)
    </br>
    </br>

```html
<!--#1. <head> 태그 안에 <script defer>를 넣었을 때 동작순서-->

<head>
  <title>body 태그 안에 script 넣기</title>
  <script defer src="main.js"></script>
  <!--defer는 Boolean으로 선언만으로 true가 된다.-->
</head>
<body></body>
```

1. html은 위에서 아래로 1줄씩 parsing 하다가
2. defer을 만나면 병렬로 script를 다운받는다.
3. html의 parsing이 끝나면 그 뒤에 script를 실행한다.

- **장점**
  - head에 넣어서 병렬적으로 동작해서 srcipt 다운받는 속도를 줄일 수 있다.
  - sciprt 다운받는 속도와 상관없이 순서대로 실행된다.
  - html의 parsing이 다 끝난 후에 script를 실행해서 html parsing하는데 속도가 다른 것들보다 빠르다.
    </br>
    </br>

### **input 태그 연결하기**

```js
uploadBtn.addEventListener("click", () => {
  const inputFile = document.querySelector(".upload-img");
  inputFile.click();
});
```

- 브라우저에 input 태그 숨기고 버튼을 누르면 input 태그가 실행될 때 사용한 코드
  </br>
  </br>

### **자식 태그 개수 가져오기**

```js
const updateList = document.querySelector(".update-info");
const updateCount = document.querySelector(".update-count");
updateCount.textContent = updateList.childElementCount;
```

- 자식 개수가 브라우저에 출력되는 코드
  </br>
  </br>

### **부모 태그 가져오기**

```js
const profileShowButton = document.querySelectorAll(".profile-show");
const parent = btn.parentNode.parentNode;
```

- parentNode를 2번 쓰면 부모의 부모를 가져올 수 있는 코드
  </br>
  </br>

### **태그에 클래스 넣기**

```js
btn.classList.toggle("profile-hidden");
```

- toggle은 클래스가 있을 땐 삭제해주고, 없을 땐 넣어주는 역할을 한다.
  </br>
  </br>

### **Destructuring 문법**

```js
// Destructuring 문법 사용 X
let num = [1, 2];
let num1 = num[0];
let num2 = num[1];

// Destructuring 문법 사용 O
let [num1, num2] = [1, 2];
```

- 간단하게 array를 각각의 변수로 빼서 쓸 수 있다.
  </br>
  </br>

### **배열의 값만 출력해서 가져오기**

```js
// Destructuring 문법 사용 X
let clothes = ["양말", "바지"];
let copyClothes = [...clothes];
```

- ...문법은 **배열의 값만 출력**해서 새로운 배열을 생성하게 해주는 문법이다.
  </br>
  </br>

### **배열 정렬하기**

```js
let arr = [1, 4, 2, 7, 5];

// 오름차순 정렬
console.log(arr.sort());

// 내림차순 정렬
arr.sort((a, b) => {
  return b - a;
});
console.log(arr);
```

- **sort(compareFunction)** compareFunction에서 리턴값이 0보다 작으면 a가 b 앞에 오도록 정렬하고,</br>
  리턴 값이 0보다 클 경우, b가 a보다 앞에 오도록 정렬한다.</br>
  만약 0을 리턴하면 a와 b 순서를 바꾸지 않는다.
  </br></br>
- 원본 배열이 정렬되고, 리턴하는 값 또한 원본 배열을 가리키고 있다는 걸 기억하자.
  </br>
  </br>

### **map() 사용하기**

```js
let arr = [1, 4, 2, 7, 5];

arr.map((item) => {
  console.log(item); // 1 4 2 7 5 (순서대로 출력된다)
});
```

- **map() 사용방법**

1. map()은 배열의 개수만큼 반복 실행한다.
2. 함수의 파라미터는 배열 안에 있던 자료이다.
3. return에 값을 적으면 배열에 담아준다. (원본 배열의 값도 변경된다.)
   </br>
   </br>

### **slice()와 splice() 차이점**

```js
let mark = ["0f", "1f", "2f", "6f"];

let sliceMark = mark.slice(0, 3);
/* 
  mark -> ['0f', '1f', '2f', '6f']
  sliceMark -> ['0f', '1f', '2f']
*/

let spliceMark = mark.splice(0, 3);
/*
  mark -> ['6f']
  spliceMark -> ['0f', '1f', '2f']
*/
```

- **slice()의 특징**

1. 처음 위치에서 몇 개까지를 복사하고 새로운 배열을 생성할 것인지 역할을 수행한다.
2. 원본 배열에 영향을 미치지 않는다.

- **splice()의 특징**

1. 처음 위치에서 몇 개까지를 지울 것인지 역할을 수행한다.
2. 원본 배열에 영향을 미친다.
   </br>
   </br>

### **클로저**

```js
let outer = function () {
  let a = 5;
  let inner = function () {
    // 외부에 있는 변수를 사용함 -> 클로저
    return ++a;
  };

  return inner;
};

let outer2 = outer();
console.log(outer2()); //6
console.log(outer2()); //7

//더이상 사용을 하지 않는다면 클로저 함수 종료해야 한다
outer = null;
```

- **클로저의 특징**

1. 어떤 함수에서 선언한 변수를 내부 함수를 외부로 전달했을 때, 실행 컨텍스트가 종료되어도 해당 변수가 사라지지 않는 현상을 말한다.

2. 메모리를 계속 차지하기 때문에 더 사용하지 않는 클로저는 종료시킬 필요가 있다.
   </br>
   </br>

### **배열 초기화하기**

```js
let reset;
(reset = []).length = 4;
reset.fill(false); //[false, false, false, false]

// 어떤 배열의 길이를 복사하고 싶을 때
let arr = ["a", "b", "c", "d", "x", "z"];

(reset = []).length = mark.length;
reset.fill(""); // ['', '', '', '', '', ''];
```

- **for이나 new Array()를 사용하지 않은 이유**
  - new Array(N)은 속도가 느리기 때문이다.
  - for문보다 훨씬 코드가 간결하고 이해하기 쉽기 때문이다.
    </br>
    </br>

### **클래스의 getter/setter**

```js
class Person {
  constructor(name, age) {
    // this는 인스턴스를 가리킨다. (인스턴스 => kim)
    this.name = name;
    this.age = age;
  }

  get age() {
    return this._age;
  }

  set age(value) {
    this._age = value;
  }
}

const kim = new Person("Kim Yong", 34);
```

- **getter/setter 사용하는 이유**

  - 값을 가져오거나 저장할 때 개발자가 아닌 다른 사용자가 임의로 수정하면 오류가 발생할 수 있기 때문이다.
    </br></br>

- **getter/setter에서 필드 명을 다르게 하는 이유**
  1. **필드명이 같으면** 생성자(constructor)에서 필드가 `매모리에 있는 값을 저장하지 않고, getter을 호출한다.`
  2. **= value** 일 때는 메모리에 있는 값을 가져오지 않고 setter을 호출한다.
  3. 이것이 계속 반복되면 `Maximum call stack size exceeded.` 라는 오류가 발생한다.
  4. 필드명이 다르면 이런 오류는 발생하지 않는다.
     </br>
     </br>

### **JS의 public과 private**

```js
class Num {
  publicNum = 123;
  #privateNum = 567;
}

const num1 = new Num();

console.log(num1.publicNum); // 123
console.log(num1.privateNum); // undefined
```

- **public과 private 특징**
  1. 생성자 없이 해당 변수를 선언할 때 사용한다.
  2. public 변수는 변수 앞에 아무것도 없고, 내부 및 외부에서도 접근이 가능하다.
  3. private 변수는 변수 앞에 **#** 가 있고, 클래스 내부에서만 접근이 가능하다.
  4. private를 호출했다고 오류는 발생하지 않고, undefined을 반환한다.
     </br>
     </br>

### **JS의 extends**

```js
class Shape {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  getArea() {
    return width * height;
  }
}

class Rectangle extends Shape {}
class Triangle extends Shape {
  getArea() {
    return (width * height) / 2;
  }
}

const rectangle = new Rectangle(20, 20);
const triangle = new Triangle(10, 6);
console.log(rectangle.getArea()); // 40
console.log(triangle.getArea()); // 30
```

- **상속(extends)의 사용 이유**

  - 클래스들 끼리 중복되는 부분을 하나의 클래스로 저장하고 상속을 하면,

  1. 유지보수가 쉬워진다.
  2. 중복되는 코드를 줄여서 가독성을 높인다.
  3. 다양한 표현이 가능해진다. `(ex: getArea()를 Triangle에 맞게 수정한 것처럼)`
     </br>
     </br>

### **JS의 instanceof**

```js
class Shape {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  getArea() {
    return width * height;
  }
}

class Rectangle extends Shape {}
class Triangle extends Shape {
  getArea() {
    return (width * height) / 2;
  }
}

console.log(Triangle instanceof Shape); //T
console.log(Triangle instanceof Rectangle); //F
console.log(triangle instanceof Triangle); //T
console.log(Triangle instanceof Object); //T
```

- **instanceof 사용방법**

  - `A instanceof B`
  - A와 B가 동일한가? 라는 의미이다.
  - 부모와 자식은 동일하다.
  - 다른 클래스끼리는 동일하지 않다.
  - JS의 모든 객체의 부모는 Object이다.

  </br>
  </br>

### **JS의 Object 생성**

```js
const user1 = { name: "coder", age: 32 };
user1.hasJob = true;
console.log(user1); // {name: 'coder', age: 32, hasJob: true}

delete user.hasJob;
console.log(user1); // {name: 'coder', age: 32}
```

- **Object 특징**
  1. key와 value로 이루어진 집합체 이다.
  2. Object가 생성된 뒤 새로운 key와 value를 넣거나 삭제할 수 있다.
  3. JS가 `Dynamic Type Language`라서 동적으로 타입이 Runtime 후에 결정되기 때문에 가능하다.
     </br>
     </br>

### **JS의 Object 호출하기**

```js
const user1 = { name: "coder", age: 32 };

// . 사용하기
console.log(user1.name);

// [] 사용하기
console.log(user1["name"]);

function printValue(obj, key) {
  // . 으로 하면 obj 안에 key라는 프로퍼티 값을 출력해줘 라는 의미가 된다.
  // console.log(obj.key);

  // []를 사용해야 정상적으로 작동한다.
  console.log(obj[key]);
}
```

- **Object 호출문 차이점**
  1. 대부분의 경우 .(점)을 사용하지만
  2. 위와 같이 key를 인자로 받아서 해당 프로퍼티 값을 출력하는 함수에는 `[]`를 사용해야 한다.
     </br>
     </br>

### **JS의 Object 반복문으로 출력하기**

```js
const user1 = { name: "coder", age: 32 };

for (key in user1) {
  console.log(key); // name age
}

for (value of user1) {
  console.log(value); // "coder" 32
}
```

- **반복문 차이점**
  1. for..in은 Object의 key를 반복적으로 출력해준다.
  2. for..of는 Object의 value를 반복적으로 출력해준다.
     </br>
     </br>

### **JS의 Object 복사하기**

```js
const user1 = { name: "coder", age: 32 };

// 방법1
const user2 = {};
for (key in user1) {
  user2[key] = user1[key];
}

// 방법2
const user3 = {};
Object.assign(user3, user1);
```

- **Object.assign 특징**

  1. Object.assign(target, source) 기본적으로 이렇게 사용한다.
  2. target에 source를 덮어씌워서 똑같은 Object를 복사하는 방법이다.
  3. 이때 target에 source와 동일한 key가 있다면, `source 것으로 덮어진다`.
     </br>
     </br>

- **Object.assign을 사용하는 이유**
  - for문보다 간결해서 요즘 많이 사용한다.
    </br>
    </br>

### Uncaught SyntaxError: Illegal return statement 오류 해결하기

```js
// 오류가 발생한 코드
if (filter != "구 선택" && keyword == "") {
  return (list = resetList.filter((store) => store.code.includes(filter)));
}

// 오류를 해결한 코드
const showContent = (filter, keyword) => {
  if (filter != "구 선택" && keyword == "") {
    return (list = resetList.filter((store) => store.code.includes(filter)));
  }
};
```

- **return문은 함수 블록 내에서만 사용할 수 있다.**

1. 자바스크립트에선 함수가 아닌 블록 내에서 사용하면 오류가 발생한다.
