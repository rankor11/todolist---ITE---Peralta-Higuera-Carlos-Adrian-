<template>
    <div class="todo-input">
        <form @submit="addTodo" >
            <input type="text" placeholder="Escribe una tarea" v-model='title'>
            <button>Agregar</button>
        </form>
    </div>
</template>

<script>
import {uuid} from 'vue-uuid'
export default {
    name: 'TodoAdd',
    data(){
        return{
            title:''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
            };
            this.title = '';
            this.$emit('add', newTodo);
            }
    }
}
</script>

<style scoped>
.todo-input{
    padding: 10px;
}

input{
    padding: 10px ;
    outline: none;
    border-radius: 8px;
    width: 80%;
    border: 2px solid #1385D4 ;
}
input:hover{
    border: 2px solid #D4135C ;
}

button {
  background-color: #2278E2 ; 
  border: none;
  color: white;
  padding: 10px 20px;
  border-radius: 8px;
  text-align: center;
  display: inline-block;
  font-size: 13px;
  margin: 11px;
  cursor: pointer;
  transition-duration: 0.4s;
  box-shadow: 0 2px 2px 0 rgba(0,0,0,0.2), 0 6px 9px 1px rgba(0,0,0,0.5);
}

button:hover{
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.575),0 17px 50px 0 rgba(0,0,0,0.19);
}
</style>