# [CSS](README.md)

### **사용자 지정 속성**

```css
:root {
  --clr-gray: rgb(172, 172, 172);
  --clr-black: #171717;
  --myProfile-marin-right: 1.4rem;
  --profile-margin-right: 0.7rem;
  --margin: 20px;
}
```

- :root 로 CSS의 변수를 생성할 수 있습니다.
  </br>
  </br>

### **요소 가운데 정렬**

```css
section {
  /* margin으로 가운데 정렬하기*/
  margin: 0 auto;

  /* grid로 가운데 정렬하기*/
  display: grid;
  place-items: center;
}
```

- grid는 안쪽에 있는 요소를 가운데 정렬 해주므로 전체를 감싸고 있는 요소에 style을 적용해야 한다.
  </br>
  </br>

### **텍스트 수평/수직 정렬**

```css
div {
  /* 수직 정렬 */
  line-height: 40px;

  /* 수평 정렬 */
  text-align: center;
}
```

- 수직 정렬은 텍스트를 div로 감싸서 line-height를 주면 된다.
  </br>
  </br>

### **이미지 크기 조정하기**

```css
.my-profile {
  width: 100px;
  height: 100px;
  border-radius: 40px;
  overflow: hidden;
  margin-right: 10px;
}

.my-profile > img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
```

- img를 감싸고 있는 태그에 원하는 크기를 입력하고 img에는 width, height에 100%를 주면서 object-fit으로 해당 크기에 어떻게 들어갈 것인지 정한다.
  </br>
  </br>

### **이미지 180도 회전하기**

```css
.btn {
  transform: rotate(180deg);
}
```

- 단위는 deg를 주고 원하는 회전 각도를 쓴다.
  </br>
  </br>

### **커서가 요소에 올라갔을 때 스타일 적용하기**

```css
.btn:hover {
  transform: rotate(180deg);
}
```

- :hover는 마우스 커서를 올리면 해당 요소에 스타일이 적용된다.
  </br>
  </br>

### **요소 배경에 이미지 넣기**

```css
.container {
  background: url(./assets/gray.png) no-repeat center/cover;
}
```

- background 속성 값에는 **색상, 이미지, 반복 여부, 위치/사이즈**를 순서대로 작성하면 된다.
  </br>
  </br>

### **부모 태그에서 자식 태그 위치 변경하기**

```css
.profile-img {
  position: relative;
}

.profile-img > .upload-button {
  position: absolute;
  top: 70%;
  left: 70%;
}
```

- absolute는 부모에 position 태그가 없으면 상위 태그 위치에 따른다.</br>그래서 부모 태그에 position을 주고 자식 태그에 top, left 위치 속성을 주면 부모 태그 크기에 따라 배치된다.
  </br>
  </br>

### **transition 사용하기**

```css
/*  style.css  */

/* 애니메이션 전 동작 */
.start {
  opacity: 0;
}

.end {
  opacity: 1;
  transition: opacity 0.5s; /* opacity가 변경될 때 0.5초에 걸쳐서 변경해주세요 */
}
```

- **transition 문법**</br>
  `transition: 스타일명 시간;` -> **스타일명이 변경**될 때 시간만큼 걸쳐서 변경해준다.

- **transition(전환애니메이션) 사용방법**

1. 애니메이션 동작 전 style 만들기
2. 애니메이션 동작 후 style 만들기
3. style에 transition 주기
4. 원할 때 2번 style 부착하기
