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

1. **&#60;template&#62; 태그**

- HTML을 사용하는 태그이다.
- 컴포넌트도 HTML 구조로 넣을 수 있다.

2. **&#60;script&#62; 태그**

- JavaScript를 사용하는 태그이다.
- components에는 컴포넌트 이름들을 쓰고, 사용할려면 import를 맨 위에 써야 한다.

3. **&#60;style&#62; 태그**

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

1. **데이터 만드는 법**

- &#60;script&#62; 태그 안에 **data()** 를 사용해서 변수를 만든다.
  </br>

2. **&#60;template&#62;에 데이터 바인딩 하는 법**

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

1. **Vue의 반복문 특징**

- Vue.js에서 반복문은 **v-for** 만 사용한다.
- React에서 사용하는 map, forEach 등과 비슷한 역할을 한다.
  </br>

2. **반복문 사용 방법**

- &#60;태그 v-for="(array내의 데이터가 들어갈 변수명, 인덱스) in array명" :key="태그의 key값" &#62;
  </br>
  </br>

### **프로젝트 생성 오류 해결**

```
PS D:\JavaScript\01\vue-project> vue create ApiTest
Invalid project name: "ApiTest"
Warning: name can no longer contain capital letters
```

1. **오류 발생 이유**

- 프로젝트 이름에 **대문자**가 들어가면 이런 오류가 발생한다.

2. **오류 해결 방법**

- 대문자로 구분하지 말고 **-**를 사용해서 구분한다.
  </br>
  </br>

### **axios로 API 요청하기**

```vue
<!-- 파일 경로: /root/.env.local -->
Vue_APP_API_KEY = api키값
```

- **API KEY 값 입력하기**

  1. .env.local 파일을 생성하고 위 코드처럼 API 키를 생성한다.
     </br>

```js
// 파일 경로: /src/main.js
import axios from "axios";
Vue.prototype.$axios = axios;
```

1. **axios를 설치한다.**

- 서버와 통신하기 위한 http통신 모듈이다.
- `npm install axios` 를 터미널에 입력한다.

2. **import axios를 한다.**

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

- **axios를 사용해서 데이터 받아오기**

  1. **created()**에서 주로 api 통신을 한다.
  2. `headears: {"app-id": process.env.VUE_APP_API_KEY}` 서버에서 **app-id라는 이름으로 너의 api key를 헤더에 담아서 보내주면 api key가 유효한지 확인하고, 데이터 보내줄게** 라는 의미이다.
     </br>
     </br>

### **받아온 api 브라우저에 보여주기**

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

1. **api 데이터를 담은 변수 생성**

- data()에 변수를 생선한다.

2. **데이터 담기**

- `this.list`를 하면 data()에 생성한 변수를 가리킨다.

3. **브라우저에 보여주기**

- &#60;template&#62;에 {{}}를 사용해서 브라우저에 보여준다.
- v-for을 사용해서 중복되는 코드를 줄인다.
  </br>
  </br>

### **컴포넌트 이름 오류**

```
Component name should always be multi-word.
```

- **Vue 컴포넌트 이름은 항상 여러 단어로 구성되어야 한다.**

1. 단일 단어로 구성된 HTML 엘리먼트와의 충돌을 방지하기 위해 `vue에서 제공하는 컴토넌트를 제외한 컴포넌트의 이름은 항상 여러 단어로 구성되어야 한다.`
   </br>
   </br>

### **props 사용해서 데이터 보내기**

```html
<!-- <PostPage />는 자식 컴포넌트 -->
<template>
  <ol v-for="item in list" :key="item.id">
    <PostPage :item="item" />
  </ol>
</template>
```

- **props 사용하는 방법**

1. 자식 컴포넌트 태그 안에 `:보내는이름="보내는데이터"`를 사용한다.
   </br>
   </br>

### **자식 컴포넌트에서 props 데이터 사용하기**

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

- **props 데이터 받아오기**

1. &#60;script&#62; 부분에 `props: ["받은이름"]`으로 배열 형식으로 작성한다.
   </br>
   </br>

### **The template requires child element 오류 해결**

```vue
<!-- 오류 해결 전 -->
<template></template>

<script></script>

<!-- 오류 해결 후 -->
<template>
  <div>
    <h1>하나 이상의 HTML 태그가 필요하다.</h1>
  </div>
</template>

<script></script>
```

1. **오류 발생 이유**

- template에 HTML 태그가 없을 때 발생한다.

2. **오류 해결 방법**

- 반드시 하나 이상의 HTML 태그를 넣으면 된다.
  </br>
  </br>

### **npm WARN EBADENGINE Unsupported engine 오류 해결**

```
npm WARN EBADENGINE Unsupported engine {
npm WARN EBADENGINE   package: '@achrinza/node-ipc@9.2.6',
npm WARN EBADENGINE   required: {
npm WARN EBADENGINE     node: '8 || 9 || 10 || 11 || 12 || 13 || 14 || 15 || 16 || 17 || 18 || 19'
npm WARN EBADENGINE   },
npm WARN EBADENGINE   current: { node: 'v20.0.0', npm: '9.6.6' }
npm WARN EBADENGINE }
```

1. **오류 발생 원인**

- `Unsupported engine`
  - node.js와 충돌이 발생했기 때문이다.

2. **오류 해결 방법**

- 제어판에서 node.js를 제거하고 재설치한다.
- `npm uninstall -g vue`와 `npm uninstall vue`로 기존에 깔아둔 vue를 지운다.
- 다시 재설치한다.
  </br>
  </br>

### **vue2와 vue3의 &#60;script&#62;의 차이점**

```js
<!-- vue2 버전 -->
<script>
export default {
  data: () => ({
    count: 0,
  }),

  method: {
    increment() {
      this.count++;
    },
  },
};
</script>

<!-- vue3 버전 -->
<script setup>
import { ref } from "vue";

const count = ref(0);

function increment() {
  count.value++;
}
</script>
```

- **vue2와 vue3에서 사용하는 API가 다르기 때문에 문법이 다르다.**

  1. vue2는 `Option API`를 활용한다.
  2. vue3는 `Composition API`를 활용한다.

- **Option API의 특징**

  1. this를 활용해서 컴포넌트 인스턴스에 접근하여 초보자들도 쉽게 적응할 수 있다.
  2. 값을 변경할 때는 `this.변수명`을 사용해야 한다.

- **Composition API의 특징**
  1. ref로 값이 변경되는 컴포넌트의 상태를 업데이트할 수 있고, 이벤트 핸들러는 일반적인 작업을 단순화되도록 도와준다.
  2. 값을 변경할 땐, `변수명.value`를 사용해야 한다.
     </br>
     </br>

### **vue2와 vue3에서 자식 컴포너틑 사용 차이점**

```vue
<!-- vue2 버전 -->
<script>
import ShowList from "./components/ShowList.vue";

export default {
  components: {
    ShowList,
  },
};
</script>

<template>
  <ShowList />
</template>

<!-- vue3 버전 -->
<script setup>
import ShowList from "./components/ShowList.vue";
</script>

<template>
  <ShowList />
</template>
```

- **vue2와 vue3에서 자식 컴포넌트를 사용할 때 차이점이 있다**

1. vue2에서는 자식 컴포넌트를 import 한 후, `components 옵션`을 사용하여 컴포넌트를 등록해야 한다.
2. vue3에서는 자식 컴포넌트를 import만 하면 된다.

</br>
</br>

### **vue2와 vue3에서 props 문법 차이점**

```js
<!-- vue2 버전 -->
<!-- 부모 컴포넌트 -->
<script>
import ShowList from "./components/ShowList.vue";

export default {
  components: {
    ShowList,
  },

  data() {
    return {
      list: [1, 2, 3, 4],
    };
  },
};
</script>

<template>
  <ShowList :item="list" />
</template>

<!-- 자식 컴포넌트-->
<script>
export default {
  props: {
    item: Object,
  },
};
</script>

<template>
  <p>{{ item }}</p>
</template>

<!-- vue3 버전 -->
<!-- 부모 컴포넌트 -->
<script setup>
import { ref } from "vue";
import ShowList from "./components/ShowList.vue";

const list = ref([1, 2, 3, 4]);
</script>

<template>
  <ShowList :item="list" />
</template>

<!-- 자식 컴포넌트 -->
<sciprt setup>
const props = difineProps({
  item: Object
})
</sciprt>

<template>
  <p>{{ item }}</p>
</template>
```

- **vue2와 vue3에서 props를 전달받은 자식컴포넌트에서 문법 차이점이 있다**

1. vue2는 `props 옵션`에 전달받은 props의 데이터형을 입력한다.
2. vue3는 `defineProps()`를 활용해서 전달받은 props의 데이터형을 입력한다. 여기서 반환된 객체는 JS에서 접근이 가능하다.
