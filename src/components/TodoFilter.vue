<template>
    <div>
        <div class="card-body d-flex justify-content-evenly">
            <button class="btn-small btn-primary-outline" @click="filter('completed')" role="button">COMPLETAS</button>
            <button class="btn-small btn-primary-outline" @click="filter('active')" role="button">PENDIENTES</button>
            <button class="btn-small btn-primary-outline" @click="filter('all')" role="button">TODAS</button>        
        </div>
    </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
export default {
    name: 'TodoFilter',
    setup() {
        const state = inject('state')
        const filter = value => {
            state.value = value
        }
        return {state, filter}
    }
}
</script>