<template>
<!--  템플릿 태그 아래 루트에는 태그가 하나만 있어야 한다. 아래 div 태그가 병렬적으로 두 개 있으면 안되고 모두 아래 div태그 안에 위치해야 함-->
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->

<!--    기존에 하던 것 처럼 등록한다. 아래 세 경우는 모두 같은 것을 의미-->
<!--    <hello-world></hello-world>-->
<!--    <HelloWorld></HelloWorld>-->
<!--    <Helloworld/>-->

    {{ str }}
<!--    v-bind:하위 컴포넌트에서 정의한 props 이름="현재 컴포넌트의 데이터 이름"-->
    <AppHeader
        v-bind:propsdata="str"
        v-on:renew="renewStr"
    />
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import로 들고 와서 아래 components에 등록해서 사용한다.
import AppHeader from './components/AppHeader.vue';

export default {
  //인스턴스 옵션 속성 or 컴포넌트 옵션 속성을 등록한다.
  // name: 'App',
  // components: {
  //   //HelloWorld
  //   // 아래와 같은 내용임
  //   // 'hello-world': HelloWorld
  // }

  // data: {
  //   기존에 하던것처럼 이런 방식으로 데이터를 정의하면 안된다. 여러 곳에서 이 데이터를 참조할 수 있기 때문에 함수로 정의해서 항상 새 객체를 반환하도록 해야함
  // }

  data: function () {
    return {
      str: 'Header'
    }
  },
  components: {
    AppHeader
  },
  methods: {
    renewStr: function () {
      this.str = 'hi';
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
