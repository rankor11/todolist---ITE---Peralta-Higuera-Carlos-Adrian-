<template>
    <div class="todo-body">
        <!--  <div v-if="todo.edit" @dblclick="$emit('edit', todo.edit)" class="todo-item">{{ todo.title }}</div> 
        <input v-else class="todo-item-edit" type="text" v-model=todo.title> -->
        <div class="elements">
            <div v-if="!edit">{{ todo.title }}</div>
            <input v-else class="todo-item-edit" type="text" v-model=todo.title>
        </div>
        <div class="buttons">
            <button @click="editTodo" class="edit">Editar</button>
            <button class="remove" @click="$emit('remove-todo', todo.id)  ">Eliminar</button>   
         </div>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props:['todo'],
    data(){
    return {
        edit: false,
    }
    },
    methods: {
        editTodo(){
            this.edit = this.edit == true ? false :true;
        }
   /* editTodo(elem){
          const todo = {
              id:elem.id,
              title:elem.title,
              edit:true
          }
          this.$emit('edit',todo);
    }*/ 
    }
}
</script> 

<style scoped>

.todo-body{
    margin: 3px;
    padding-top: 8px;
    display: inline-block;
    vertical-align: top;
    border-radius: 8px;
    background-color: #ededef ;
    width: 99%;
    max-height: 90px;
    text-indent: 10px;
    box-shadow: 0 1px 1px 0 rgba(0, 0, 0, 0.59);
}

.elements, .buttons{
display:inline-block;
}

.elements{
    width: 400px;
}

.buttons{
    width: 165px;
}

.edit {
  background-color: #13A8D4 ; 
  border: none;
  color: white;
  padding: 8px 12px;
  border-radius: 8px;
  text-align: center;
  display: inline-block;
  font-size: 13px;
  cursor: pointer;
  margin-right: 10px;
  margin-bottom: 10px;
  transition-duration: 0.4s;
  box-shadow: 0 2px 2px 0 rgba(0,0,0,0.2), 0 6px 9px 1px rgba(0,0,0,0.5);
}

.edit:hover{
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.575),0 17px 50px 0 rgba(0,0,0,0.19);
}

.remove{
  background-color: #D4135C ; 
  border: none;
  color: white;
  padding: 8px 15px;
  border-radius: 8px;
  text-align: center;
  display: inline-block;
  font-size: 13px;
  cursor: pointer;
  transition-duration: 0.4s;
  box-shadow: 0 2px 2px 0 rgba(0,0,0,0.2), 0 6px 9px 1px rgba(0,0,0,0.5);
}

.remove:hover{
  box-shadow: 0 12px 16px 0 rgba(0, 0, 0, 0.575),0 17px 50px 0 rgba(0,0,0,0.19);
}

input{
    border-radius: 8px;
    background-color: #ededef ;
    text-indent: 5px;
    font-size: 1em;
    box-shadow: 0 1px 1px 0 rgba(0, 0, 0, 0.59);
    border-radius: 8px;
    border: 2px solid #1385D4 ;
    width: 350px;
   
}

input:hover{
    border: 2px solid #D4135C ;
}

</style>