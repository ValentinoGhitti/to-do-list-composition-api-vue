<template>

    <li 
        class="list-group-item d-flex alert alert-success justify-content-between"
        :class="{'strike-through': todo.state}"
    >
        <span 
            role="button" 
            @click="changeState(todo.id)" 
        ><h5>{{todo.text}}</h5>
        </span>
        <div role="button" @click="deleteTask(todo.id)">
            <i class="fa-solid fa-xmark"></i>
        </div>
    </li>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    props: {
        todo: {
            type: Object,
            required: true
        }
    },
    setup() {
        const todos = inject('todos')
        const deleteTask = id => {
            todos.value = todos.value.filter(item => item.id !== id)
        }
        //guarda
        const changeState = id => {
            todos.value = todos.value.map(item => {
                if(item.id === id){
                    item.state = true
                }
                return item
            })
        }
        return {deleteTask, changeState}
    }
}
</script>

<style>
.strike-through {
    text-decoration: line-through;
    background-color: lightgreen ;
}
li {
    overflow: hidden;
}
ul li:before {
    content: none;
}
</style>