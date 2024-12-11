<template>
  <form v-on:submit.prevent="submitForm"> 
    <div>
      <label for="username"> id: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password"> pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit" >login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: () => ({
    username: '',
    password: '',

  }),
  methods: {
    submitForm: function() {
      // event.preventDefault(); //코드의 새로고침을 막아줌. --> 기본적인 js에서 사용 
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)
      .then(function(respose){
        console.log(respose);
      })
      .catch(function(error){
        console.log(error);
      });
    }
  }
}
</script>

<style>

</style>