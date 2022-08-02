<template>
    <form class="form-group" @submit.prevent="form">
        <div class="d-flex justify-content-between">
            <h4 class="text-danger text-sm-3" for="paperInputs1">Lista de tareas para la semana</h4>
        </div>
        <input 
            type="text"
            id="paperInputs1"
            class="  input-block"
            placeholder="ingrese la tarea"
            v-model.trim="text"
        >
    </form>
</template>

<script>
import { inject, ref } from 'vue'

export default {
    setup() {
        const todos = inject('todos')
        const text = ref('')
        
        const form = () => {
            if(text.value === ''){
                return 
            }
            const todo = {
                text: text.value,
                state: false,
                id: Date.now()
            }
            todos.value.push(todo)
            text.value = ''
        }
        return {form, text}
    }
}
</script>

<style>
h4 {
    text-decoration:underline;
}
</style>