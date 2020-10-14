<template>
    <div>
    <ul>
       <li v-for="(data,i) in jsonData" :key="i">
           {{data.name}} <br> 
           {{data.addr_new}} <br>
           전화예약: {{data.call_num}} <br>
           <br>
        </li>
     </ul>
    </div>
</template>
<script>
import golfplace from '../assets/data/골프장.json';

export default {
    // name:'App',
    data(){
        this.jsonData=[]
    },
    mounted () {
       this.loadJsonData();
    },
    methods: {
       loadJsonData(){
          setTimeout(()=>{
             this.jsonData =golfplace
            }, 300)
        }
    }
}
</script>
<style>

</style>