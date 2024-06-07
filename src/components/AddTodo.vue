<template>
    <form id="form" @submit.prevent="onSubmit">
        <div>
            <input
                v-model="text"
                type="text"
                placeholder="Todo Text.."
            />
        </div>

        <div class="mt-2">
            <button>Add Todo</button>
        </div>
    </form>
</template>

<script setup>
import {ref,defineEmits} from "vue";

const text =ref("")
const emit = defineEmits(["addTodo"])
const onSubmit=()=>{
    const todo={
        id:crypto.randomUUID(),
        text:text.value,
        complete:false
    }
    emit("addTodo",todo)}
</script>