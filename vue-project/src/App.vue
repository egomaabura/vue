<script setup>
import { ref } from 'vue';
import TodoList from '@/TodoList.vue'

const count = ref(0)
const message = ref('Hello Vue!!')
const titleClass = ref('title')
const text = ref('')
const awesome = ref(true)

function increment(){
  count.value++
}
function toggleColor(){
    if (titleClass.value){
        titleClass.value = ''
    }else{
        titleClass.value = 'title'
    }
}
function toggleAwesome(){
    awesome.value = !awesome.value
}
</script>

<template id="app">
    <section>
        <h1>{{ message }}</h1>
        <h1>{{ message.split('').reverse().join('') }}</h1>
        <button @click="increment">count: {{ count }}</button>
    </section>
    <section>
        <button @click="toggleColor">色切り替え</button>
        <h1 :class="titleClass">Make me red</h1>
    </section>
    <section>
        <input v-model="text" placeholder="Type here" />
        <p>[{{ text || 'No text' }}]</p>
    </section>
    <section>
        <button @click="toggleAwesome">Vue切り替え</button>
        <h1 v-if="awesome">Vue is awesome!!</h1>
        <h1 v-else>Oh no...😢</h1>
    </section>
    <section>
        <TodoList/>
    </section>
</template>

<style scoped>
.title {
    color: red
}
section {
    margin-top: 2em
}
</style>
