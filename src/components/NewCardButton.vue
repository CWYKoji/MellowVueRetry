<script setup>

import { ref } from 'vue';
import IconSmallPlus from './icons/IconSmallPlus.vue'

const emit = defineEmits(['create'])

const name = ref(null)
const creating = ref(false)

const create = () => {
    name.value = null
    creating.value = ! creating.value
}

const save = () =>{
    if(name.value !== null && name.value.trim() !== ''){
        emit('create', name.value)
        name.value = null
        creating.value = false
    }
}

</script>

<template>

    <div>
        <a class="butAddCard" href="#" @click.prevent="create">
            <IconSmallPlus/>
            Add
        </a>
        <input v-if="creating" type="text" v-model="name" placeholder="Title" @keypress.enter="save"/>
    </div>
</template>

<style scoped>
.butAddCard{
  display: flex;   
  align-self: center;
}

</style>