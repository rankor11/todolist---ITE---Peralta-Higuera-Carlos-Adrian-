<template>
    <div>
        <div v-bind:key="todo.edit" v-for="todo in todoslist">
            <TodoItem v-bind:todo="todo" v-on:edit="$emit('edit',todo.edit)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
  
export default {
    name: 'Todo',
    props: ['todoslist'],
    components: {TodoItem}
}
</script>
<style>

</style>

