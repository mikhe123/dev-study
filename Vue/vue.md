노션 링크 <br>
https://www.notion.so/1-8ad3188ff3614dd4961955ac1739690c

### vue는 웹프론트엔드 프레임워크

- 컴포넌트 기반의 spa(Single Page Application)을 구축할 수 있게 해주는 프레임워크

### 컴포넌트

- 웹을 구성하는 로고, 메뉴바, 버튼, 모달 창 등 웹 페이지내의 다양한 ui요소를 재사용 가능하도록 구조화 한 것

### SPA (Single Page Application)

- 단일 페이지 어플리케이션
- 하나의 페이지 안에서 필요한 영역 부분만 로딩되는 형태
- 빠른 페이지 변화
- 적은 트래픽 양

단점은 크기가 크면 *초기로딩이 느릴수 있음*

## 환경설정

### **vue cli(Command Line Interface)**툴 이용

→ 터미널 통해서 텍스트명령어 입력하는 방식

이거 이용하면 프로젝트 세팅 자동으로 해줌(프로젝트 폴더구조나 library 다운)

### Visual Studio Code 이용

→ VsCode 터미널에서 `npm install -g @vue/cli` 하면 vue cli 설치된다 (Termianl 단축 키 ctrl + ` )

npm 안되는 사람들은 node.js 안깔려 있는것

→ node.js 설치 방법 :  [https://javacpro.tistory.com/62](https://urmaru.com/9)  

- 깔았는데도 에러 나오는 경우

    ```
    Error 
    npm : 'npm' 용어가 cmdlet, 함수, 스크립트 파일 또는 실행할 수 있는 
    프로그램 이름으로 인식되지 않습니다. 이름이 정확한지 확인하고 
    경로가 포함된 경우 경로가 올바른지 검증한 다음 다시 시도하십시오.
    ```

     → terminal powershell로 되어있으면 다른것으로 바꿔주기 + vs code 껐다 켜기

Terminal 에 입력

→ `vue create 폴더명` (폴더명 test로 했음) : 프로젝트 만드는 것

→ Enter 눌러서 `default`로 설치

→ `cd test` 입력해서 test프로젝트 폴더로 이동

→ `npm run serve` 입력 해 서버 실행

```
App running at:
  - Local:   http://localhost:8080/
  - Network: http://172.30.1.18:8080/
```

여기서 [localhost:8080](http://localhost:8080) ctrl+click 했을 때 (Welcome to Your Vue.js App)페이지 나오면 정상적으로 잘 된것

## 모듈 설치

vue 라우터 설치 

vue에서 라우팅 기능 구현할 수 있도록 지원해주는 공식 library

라우팅 : 웹페이지 간 이동할 수 있도록 해주는 것

일반적인 경우 서버에 요청 → 페이지 받아옴 

라우터는 spa 원페이지 → 미리 해당하는 application 다 받아놓고 라우팅 이용 그 부분만 화면 갱신

terminal → `npm install vue-router --save`

src의 components 폴더 안에 layout폴더 생성하기

갱신 할 필요가 없는 고정 layout 으로 header부터 만듬

layout 폴더 안에 Header.vue파일 만들기

bootstrap 사용 

[https://bootstrap-vue.org/](https://bootstrap-vue.org/) → get started 누르고 아래페이지로 이동하면 module 설치방법 나와있음 

terminal → `npm install vue bootstrap bootstrap-vue`

main.js에 (import App from './App.vue' 밑에 추가)

```jsx
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

// Import Bootstrap an BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

// Make BootstrapVue available throughout your project
Vue.use(BootstrapVue)
// Optionally install the BootstrapVue icon components plugin
Vue.use(IconsPlugin)
```

Header.vue 

```jsx
<template>

</template>
<script>
export default{
        
}
</script>
```

[https://bootstrap-vue.org/](https://bootstrap-vue.org/)  페이지에서 component→ Navbar이동해서  Nav bar 긁어오기



```jsx
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">NavBar</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#">Link</b-nav-item>
        <b-nav-item href="#" disabled>Disabled</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">ES</b-dropdown-item>
          <b-dropdown-item href="#">RU</b-dropdown-item>
          <b-dropdown-item href="#">FA</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
```

 <script수정

```jsx
<script>
export default{
        name: "header",
};
</script>
```

src에 views라는 폴더 만들기

App.vue

[localhost](http://localhost) 연결되었을 때 나온 화면 → 수정

```jsx
<script>
import Header from './components/layout/Header.vue'

export default {
  name: 'App',
  components: { // import한 Header 사용위해서 component에 Header 넣어줘야함
    Header
  }
}
</script>
```

```jsx
<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> //**이부분 삭제
		<Header />  // 이부분 추가**
  </div>
</template>
```
![Untitled](https://user-images.githubusercontent.com/78526031/117561084-8d947380-b0ce-11eb-9496-7e998dbba78b.png)