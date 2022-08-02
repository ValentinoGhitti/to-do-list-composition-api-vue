<template>
    <ul class="list-group">
        <todo-item 
            v-for="todo in todos" 
            :key="todo.id"
            :todo="todo"
            class="alert-warning text-dark fs-6"
        />
        <li class="list-group" v-if="todos.length === 0">
            <h3>No hay tareas :D</h3>
            <div class="d-flex justify-content-center">
                <img 
                    class="draw float- no-border" 
                    src="../../public/img/draw.png" 
                    alt="draw"
                >
            </div>
        </li>
        <div class="mt-5" v-if="todos.length !== 0">
            <todo-footer />
            <div class="mt-5">
                <todo-filter />
            </div>
        </div>
    </ul>
</template>

<script>
import { ref, computed, inject, provide } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFilter from './TodoFilter.vue'
export default {
    name: 'TodoList',
    components: {
        TodoItem,
        TodoFooter,
        TodoFilter
    },
    setup() {
        const todosAll = inject('todos')
        const state = ref('all')
        const todos = computed(() => {
            if(state.value === 'all') {
                return todosAll.value
            }
            if(state.value === 'active') {
                return todosAll.value.filter(item => item.state === false)
            }
            if(state.value === 'completed') {
                return todosAll.value.filter(item => item.state === true)
            }
        })
        provide('state', state)
        return {todos}
    }
}
</script>

<style scoped>
.draw {
    height: 120px;
    width: 150px;
}
</style>