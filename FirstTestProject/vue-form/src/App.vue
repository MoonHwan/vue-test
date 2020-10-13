<template>
  <!-- <form v-on:submit="submitform"> -->
  <form v-on:submit.prevent="submitform">
    <!-- prevent=form의 기본 기능(새로고침)을 막는다 -->
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username">
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password">
    </div>
    <button type="submit">login</button>
    <p>{{username}}가 로그인했음</p>
  </form>
</template>

<script>
import axios from 'axios';
export default {
  data:function(){
    return{
      username:'',
      password:''
    }
  },
  methods:{
    submitform: function(){
      // event.preventDefault(); //새로고침 막음
      console.log(this.username,this.password);
      var url='https://jsonplaceholder.typicode.com/users';
      var data={
        username:this.username,
        password:this.password
      }
      axios.post(url, data)
        .then(function(response){
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        })
    } 
  }
}
</script>

<style>

</style>
