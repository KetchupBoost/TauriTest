<script setup lang="ts">
import { v4 as uuidv4 } from "uuid";
import { ref } from "vue";

interface Todo {
    id: string;
    todo: string;
}

const todos = ref<Todo[]>([]);
const todo  = ref("");


const add = () => {
    todos.value.push({
        id: uuidv4(),
        todo: todo.value
    })
}

function test<T>(a: T){}
test<string>("")

const del = (index: number) => {
    todos.value.splice(index, 1);
}
</script>

<template>
    <div>
        <form @submit.prevent="add">
            <input v-model="todo" />
            <button type="submit">Add</button>
        </form>
        <div 
        v-for="(todo, index) of todos"
        :key="todo.id"
        >
            {{ todo.todo }}
            <button @click="del(index)">delete</button>
        </div>
    </div>
</template>

<style scoped>

</style>