# [HTML](README.md)

### **input 태그 종류**

```html
<input type="text" minlength="1" maxlength="20" />
<input type="email" placeholder="Your Email" />
<input type="number" />
<input type="file" accept=".png, .jpg, .gif" />
<input type="checkbox" />
<input type="radio" />
```

</br>
</br>

### **aside 태그**

```html
<aside class="banner">
  <img src="./assets/도시락 이벤트 작게또.png" alt="도시락 이벤트 배너" />
</aside>
```

- 배너를 만들 때 aside 같은 시맨틱 태그로 가독성을 키우기 위해서 사용한다.
  </br>
  </br>

### **button 태그**

```html
<!-- 작동만 할 땐 type="button" 사용한다. -->
<button type="button"></button>

<!-- 제출할 때 type="submit" 사용한다. -->
<button type="submit"></button>

<!-- 초기화할 때 type="reset" 사용한다. -->
<button type="reset"></button>
```

- button을 사용할 때 무조건 type을 적어줘야 웹표준에 맞게 작성하는 것이다.
  </br>
  </br>

### **img 태그**

```html
<img src="./assets/party.jpg" alt="파티" />
```

- alt를 작성할 때 img에 의미가 중요하지 않을 때는 alt=""로 남겨둔다.
  </br>
  </br>

### **ol, ul 태그**

```html
<ol>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ol>

<ul>
  <li>바나나</li>
  <li>키위</li>
  <li>사과</li>
</ul>
```

- **ol 태그**는 순서가 중요한 리스트에 사용하고, **ul 태그**는 순서가 중요하지 않은 리스트에 사용한다.
  </br>
  </br>
