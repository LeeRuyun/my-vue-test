<template>
    <ul v-if="todos.length>0">
        <li v-for="todo in todos" :key="todo.id" class="flex gap-3 my-2">
            <button class="w-5" @click="deleteTodo(todo.id)">x</button>
            <button class="w-5" @click="completeTodo(todo.id)">v</button>
            <p :class="{'line-through' : todo.complete}">{{ todo.text }}</p>
        </li>
    </ul>
    <p v-else>No todos found.</p>
</template>

<script setup>
import {defineProps,defineEmits} from "vue"

defineProps({
    todos:{
        type:Array
    }
})
const emit = defineEmits(['deleteTodo','completeTodo'])

const deleteTodo=(todoId)=>{
    emit('deleteTodo',todoId)
}
const completeTodo=(todoId)=>{
    emit('completeTodo',todoId)
}
</script>