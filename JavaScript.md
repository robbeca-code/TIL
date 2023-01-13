# [JavaScript](README.md)

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
