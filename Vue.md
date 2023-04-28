# [Vue](README.md)

### **App.vue 구조 설명**

```vue
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
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
  </br>
  </br>

### 프로젝트 생성 오류 해결

```
PS D:\JavaScript\01\vue-project> vue create ApiTest
Invalid project name: "ApiTest"
Warning: name can no longer contain capital letters
```

1. 오류 발생 이유

- 프로젝트 이름에 **대문자**가 들어가면 이런 오류가 발생한다.

2. 오류 해결 방법

- 대문자로 구분하지 말고 **-**를 사용해서 구분한다.
  </br>
  </br>

### axios로 API 요청하기

```vue
<!-- 파일 경로: /root/.env.local -->
Vue_APP_API_KEY = api키값
```

1. API KEY 값 입력하기

- .env.local 파일을 생성하고 위 코드처럼 API 키를 생성한다.
  </br>

```js
// 파일 경로: /src/main.js
import axios from "axios";
Vue.prototype.$axios = axios;
```

1. axios를 설치한다.

- 서버와 통신하기 위한 http통신 모듈이다.
- `npm install axios` 를 터미널에 입력한다.

2. import axios를 한다.

- 각 컴포넌트마다 import axios를 하지 않고, this.$axios를 해서 axios를 가져올 수 있도록 main.js에 위 코드를 입력한다.
  </br>

```js
// 파일경로: /src/App.vue
<script>
  export default {
    name: "APP",
    created() {
      this.$axios.get("https://dummyapi.io/data/v1/post", {
        headers: { "app-id": process.env.VUE_APP_API_KEY },
      })
      .then((response) => {
        console.log(response);
      })
      .catch((error) => {
        console.log(error);
      });
    }
  }
</script>
```

1. axios를 사용해서 데이터 받아오기

- **created()**에서 주로 api 통신을 한다.
- `headears: {"app-id": process.env.VUE_APP_API_KEY}` 서버에서 **app-id라는 이름으로 너의 api key를 헤더에 담아서 보내주면 api key가 유효한지 확인하고, 데이터 보내줄게** 라는 의미이다.
  </br>
  </br>

### 받아온 api 브라우저에 보여주기

```vue
<template>
  <ol>
    <li v-for="item in list" :key="item.id">
      <h3>{{ item.text }}</h3>
      <img :src="item.image" alt="item.text" />
    </li>
  </ol>
</template>

<script>
export default {
  name: "APP",
  data: () => ({
    list: [],
  }),
  created() {
    this.$axios
      .get("https://dummyapi.io/data/v1/post", {
        headers: { "app-id": process.env.VUE_APP_API_KEY },
      })
      .then((response) => {
        this.list = response.data.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
```

1. api 데이터를 담은 변수 생성

- data()에 변수를 생선한다.

2. 데이터 담기

- `this.list`를 하면 data()에 생성한 변수를 가리킨다.

3. 브라우저에 보여주기

- &#60;template&#62;에 {{}}를 사용해서 브라우저에 보여준다.
- v-for을 사용해서 중복되는 코드를 줄인다.
  </br>
  </br>

### 컴포넌트 이름 오류

```
Component name should always be multi-word.
```

1. Vue 컴포넌트 이름은 항상 여러 단어로 구성되어야 한다.

- 단일 단어로 구성된 HTML 엘리먼트와의 충돌을 방지하기 위해 `vue에서 제공하는 컴토넌트를 제외한 컴포넌트의 이름은 항상 여러 단어로 구성되어야 한다.`
  </br>
  </br>

### props 사용해서 데이터 보내기

```html
<!-- <PostPage />는 자식 컴포넌트 -->
<template>
  <ol v-for="item in list" :key="item.id">
    <PostPage :item="item" />
  </ol>
</template>
```

1. props 사용하는 방법

- 자식 컴포넌트 태그 안에 `:보내는이름="보내는데이터"`를 사용한다.
  </br>
  </br>

### 자식 컴포넌트에서 props 데이터 사용하기

```vue
<template>
  <li>
    <img :src="item.image" alt="" />
    <div>
      <div>{{ item.text }}</div>
      <div>❤️{{ item.likes }}</div>
    </div>
    <div>{{ item.owner.lastName }}, {{ item.owner.firstName }}</div>
  </li>
</template>

<script>
export default {
  props: ["item"],
};
</script>
```

1. props 데이터 받아오기

- &#60;script&#62; 부분에 `props: ["받은이름"]`으로 배열 형식으로 작성한다.
