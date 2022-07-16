<template>
  <!-- <form v-on:submit="submitForm"> -->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
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
  name: 'App',
  data() {
    return {
      username: '',
      password: '',
    };
  },
  components: {

  },
  methods: {
    // submitForm(event) { // event는 submit 이벤트
    submitForm() {
      // submit 이벤트 시 새로고침 되는것 막음
      // event.preventDefault(); // js 방식
      console.log(this.username, this.password);

      const url = 'https://jsonplaceholder.typicode.com/users';
      const data = {
        username: this.username,
        password: this.password
      };
      axios.post(url, data)
          .then(function(response) {
            console.log(response);
          })
          .catch(function(error) {
            console.log(error);
          });
    },
  },
}
</script>

<style>

</style>
