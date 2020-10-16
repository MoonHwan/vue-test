<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input v-on:addTodo="addTodo"></todo-input>
    <!-- <todo-input v-on:하위컴포넌트에서 발생시킨 이멘트 이름="현재 컴포넌트의 매서드 명"></todo-input> -->
    <todo-list v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></todo-list>
    <!-- <todo-list v-bind:내려보낼 트롭스 속성이름="현재컴포넌트 데이터 속성" v-on:removeTodo="removeTodo"></todo-list> -->
    <todo-footer v-on:removeAll="clearAll"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data(){
    return{
      todoItems:[]
    }
  },
  methods:{
      addTodo(todoItem){
        localStorage.setItem(todoItem,todoItem);
        this.todoItems.push(todoItem);
      },
      clearAll(){
        localStorage.clear();
        this.todoItems=[];
      },
    
      clearInput(){
            this.newTodoItem='';
      },
      removeTodo(todoItem,i){
        localStorage.removeItem(todoItem); //로컬데이터 삭제하는 api
        this.todoItems.splice(i,1); //배열의 특정인덱스 삭제하는 api
      }
  },
  created(){
        if(localStorage.length>0){
            for(var i=0;i<localStorage.length;i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
  components:{
    'TodoHeader':TodoHeader,
    'TodoInput':TodoInput,
    'TodoList':TodoList,
    'TodoFooter':TodoFooter,
  }
  
}
</script>

<style>
  body{
    text-align: center;
    background-color: aliceblue;
  }
  input{
    border-style: groove;
    width: 200px;
  }
  button{
    border-style: groove;
  }
  .shadow{
    box-shadow: 5px 1px 10px rgba(red, green, blue, alpha);
  }
</style>
