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
