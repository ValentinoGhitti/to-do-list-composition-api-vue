<template>
    <h2 class="mt-3 mb-3">Cosas por hacer</h2>
    <div class="container">
        <div class="wrapper">
            <div class="paper-2">
                <div class="bg-dark d-flex">
                    <a class="no-border" href="https://github.com/ValentinoGhitti"><img class="tape no-border" src="../../public/img/cinta.png" alt=""></a>
                </div>
                <div class="p-5">
                    <todo-form />
                    <p><todo-list /></p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { provide, ref, watchEffect } from 'vue'
import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'
export default {
    components: { 
        TodoForm,
        TodoList
    },
    setup() {
        const todos = ref([])
        provide('todos', todos)
        watchEffect(() => {
        })
    }
}
</script>
<style scoped>

*{
    box-sizing:border-box;
}

a {
    background-image: none;
}

img {
    cursor: pointer;
}
.tape {
    height: 100px;
}

.wrapper{
    display:flex;
    justify-content:space-around;
}
.paper-2 {
    width:800px;
    height:100%;
    font-size: 24px; 
    background-image: linear-gradient(to bottom, #bbb 2px, #ffe5f8 0);
    background-size: 100% 19%;
}
@media screen and (max-width: 320px) {
    .paper-2 {
        width:319px;
    }
}

@media screen and (max-width: 425px) {
    .paper-2 {
        width:400px;
    }
}


@media screen and (max-width: 768px) {
    .paper-2 {
        width:400px;
    }
}
</style>