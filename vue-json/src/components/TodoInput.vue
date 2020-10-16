<template>
    <div class="inputBox shadow">
        <!-- <input type="text" v-model="newTodoTitle">  -->
        <input type="text" v-model="newTodoItem" placeholder="what todo" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
        <!-- <br> -->
        <!-- <button v-on:click="addTodo">추가</button> -->
        <modal v-if="showModal" @close="showModal=false">
            <h3 slot="header" >WORNING</h3>
            <h2 slot="body">문자를 입력해주세요 </h2>
            <span slot="footer" @click="showModal=false">닫기
                <i class="closeModalBtn fa fa-times" aria-hidden="true"></i>
            </span>
        </modal>   
    </div>
</template>
<script>
import Modal from './common/Modal.vue' 

export default {
    props:['propsdata'],
    data(){
        return{
            // newTodoTitle:'',
            newTodoItem:'',
            showModal:false
        }       
    },
    methods:{
        addTodo(){
            if(this.newTodoItem!==""){
            // console.log(this.newTodoItem)
                var value=this.newTodoItem && this.newTodoItem.trim(); //앞뒤공백제거
                this.$emit('addTodo',value);
                // localStorage.setItem(value,value);
                this.clearInput();
            } else{
                this.showModal=!this.showModal;
            }
        },
        clearInput(){
            this.newTodoItem='';
        }
    },
    components:{
        Modal:Modal
    }      
}
</script>

<style scoped>
    input:focus{
        outline: none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{ 
        float: right;
        background:linear-gradient(to right,#6478FB,#8763FB);
        display: block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn{
        color: white;
        vertical-align: middle;
    }
</style>