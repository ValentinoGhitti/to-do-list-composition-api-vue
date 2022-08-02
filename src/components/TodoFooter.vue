<template>
    <li class="d-flex justify-content-around">
        <span>Tareas pendientes : {{count}} </span>
        <button class="btn-small paper-btn btn-danger-outline" role="button" @click="deleteCompleteTask">
            Eliminar tareas realizadas
        </button>
    </li>
</template>

<script>
import { inject, computed } from 'vue'
export default {
    name: 'TodoFooter',
    setup() {
        const todos = inject('todos')
        const count = computed(() => {
            return todos.value.filter(item => item.state === false).length
        })
        const deleteCompleteTask = () => {
            todos.value = todos.value.filter(item => item.state === false)
        }
        return {count, deleteCompleteTask}
    }
}
</script>