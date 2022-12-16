<script setup>
import { ref } from 'vue';
import IconNewFile from './icons/IconNewFile.vue'

const emit = defineEmits(['create'])


const create =() => {
    emit('create')
}

</script>

<template>
    <div>
        <a class="butAddList" @click.prevent="create">
            <IconNewFile/>
            Add List
        </a>
    </div>
</template>

.butAddList{
    display: flex;   
    align-self: center;
    margin-left: 10px;
  }