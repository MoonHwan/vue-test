<template>
    <section>
        <ul>
            <li v-for="(todoItem,i) in propsdata" :key="i" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{todoItem}}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, i)">
                    <i class="fa fa-trash" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>
<script>
export default {
    // data(){
    //     return{
    //         todoItems:[]
    //     }
    // },
    props:['propsdata'], //propsdata속성에 props로 전달
    // created(){
    //     if(localStorage.length>0){
    //         for(var i=0;i<localStorage.length;i++){
    //             this.todoItems.push(localStorage.key(i));
    //         }
    //     }
    // },
    methods:{
        removeTodo(todoItem,i){
            this.$emit('removeTodo',todoItem,i)
            // localStorage.removeItem(todoItem); //로컬데이터 삭제하는 api
            // this.todoItem.splice(i,1); //배열의 특정인덱스 삭제하는 api
            //// console.log(todoItem,i);
        }
    }
}
</script>
<style scoped>
    ul{
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }
    li{
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
                                                                                                                                                                                                                                                                                                                                                                               
    .checkBtn{
        line-height: 45px;
        color: darkcyan;
    }
    .removeBtn{
        margin-left: auto;
        color: darkred;
    }
</style>