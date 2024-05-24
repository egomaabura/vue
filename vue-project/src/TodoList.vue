<script setup>
import { ref } from 'vue'

let id = 0

const newTodo = ref('')
const todos = ref([
    { id: id++, text: 'Lern HTML'},
    { id: id++, text: 'Lern JavaScript'},
    { id: id++, text: 'Lern Vue'},
    ])

function addTodo(){
    todos.value.push({
        id: id++,
        text: newTodo.value
    })
    newTodo.value = ''
}
function removeTodo(todo){
    todos.value = todos.value.filter((t) => t.id !== todo.id)
}
</script>

<template id="todo-list">
    <form @submit.prevent="addTodo">
        <input v-model="newTodo" required placeholder="New Todo">
        <button>Add Todo</button>
    </form>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.text }}
            <button @click="removeTodo(todo)">消去</button>
        </li>
    </ul>
</template>