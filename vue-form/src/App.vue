<template>
<!--  버튼이 submit 타입으로 되어 눌리면 이벤트가 form으로 올라온다. 여기서 v-on으로 submit이벤트를 받아서 submitForm메서드 실행-->
<!--  여기 .prevent는 자바스크립트의 event.preventDefault()와 동일한 기능-->
  <form v-on:submit.prevent="submitForm">
    <div>
<!--      username으로 어떤 input에 대한 label인지 나타낼 수 있음-->
      <label for="username">id: </label>
<!--      v-model을 통해 data의 값이 변할 때 화면에 반영할 수 있고, 화면에 값이 바뀌면 데이터도 바꿀 수 있는 two-way binding이 가능-->
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function () {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    submitForm: function () {
      //event.preventDefault(); //버튼을 눌러 submit 이벤트가 발생하면 자동으로 새로고침이 되는데, 바닐라 자바스크립트에서 이걸 막는 기능
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
          .then(function (response) {
            console.log(response);
          })
          .catch(function (error) {
            console.log(error);
          });
    }
  }
}
</script>

<style>
</style>
