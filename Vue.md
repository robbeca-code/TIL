# [Vue](README.md)

### **App.vue 구조 설명**

```vue
<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue"

export default {
  name: "App",
  components: {
    HelloWorld
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -mox-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

1. &#60;template&#62; 태그

- HTML을 사용하는 태그이다.
- 컴포넌트도 HTML 구조로 넣을 수 있다.

2. &#60;script&#62; 태그

- JavaScript를 사용하는 태그이다.
- components에는 컴포넌트 이름들을 쓰고, 사용할려면 import를 맨 위에 써야 한다.

3. &#60;style&#62; 태그

- CSS의 코드를 사용하는 태그이다.
  </br>
  </br>

### **데이터 바인딩**

```vue
<template>
  <div>
    <h4 :style="phoneU">갤럭시 S3 Ultra</h4>
    <!-- src/assets/images/phoneU.png 의 절대경로 -->
    <img :src="@/assets/images/phoneU.png" />
    <p>{{ priceU }} 만원</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      priceU: 136,
      phoneU: "color : blue",
    };
  },
  components: {},
};
</script>
```

1. 데이터 만드는 법

- &#60;script&#62; 태그 안에 **data()** 를 사용해서 변수를 만든다.
  </br>

2. &#60;template&#62;에 데이터 바인딩 하는 법

- {{변수명}}을 HTML 태그 안에 넣어준다.
- 속성은 `:속성="데이터명"`을 넣는다.
- 이미지 속성을 하고 싶을 땐 `:src=""`를 해야 한다.
  </br>
  </br>

### **반복문**

```vue
<template>
  <a v-for="v in menus" :key="v"> {{ v }}</a>
  <div v-for="(v, i) in titles" :key="i">
    <h4 :style="title">{{ titles[i] }}</h4>
    <p>{{ price[i] }} 만원</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      titles: ["갤럭시 S3 Ultra", "갤럭시 S3+"],
      price: [136, 130],
      menus: ["Home", "Shop", "About"],
    };
  },
  components: {},
};
</script>
```

1. Vue의 반복문 특징

- Vue.js에서 반복문은 **v-for** 만 사용한다.
- React에서 사용하는 map, forEach 등과 비슷한 역할을 한다.
  </br>

2. 반복문 사용 방법

- &#60;태그 v-for="(array내의 데이터가 들어갈 변수명, 인덱스) in array명" :key="태그의 key값" &#62;
