<template>
  <div>
    <app-header 
    v-bind:propsdata="str"
    v-on:renew="renewStr"></app-header>
    <golf-place>{{data}}</golf-place><br>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import GolfPlaceVue from './components/GolfPlace.vue';

export default {
  data:function(){
   return{
     str:'Header'
   } 
  },
   components:{
    'app-header':AppHeader,
    'golf-place':GolfPlaceVue
  },
  methods:{
    renewStr:function(){
      this.str='hi';
    },
  }
}
</script>