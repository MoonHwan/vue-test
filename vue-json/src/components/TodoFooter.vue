<template>
    <div class="clearALlContainer">
        <span class="clearAllBtn" @click="clearTodo">모두 다 지워</span>    
    </div>
</template>
<script>
export default {
    methods:{
        clearTodo(){
            this.$emit('removeAll');
            // localStorage.clear();
        }

    }
}
</script>
<style scoped>
    .clearALlContainer{
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: darkseagreen;
        border-radius: 5px;
        margin: 0 auto;
    }
    .clearAllBtn{
        color:blue;
        display: black;
    }
</style>