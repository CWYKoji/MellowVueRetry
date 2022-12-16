<script setup>
import Modal from'./Modal.vue'
import { ref } from 'vue'

const isModalOpen = ref(false)


const openModal = () =>{
    isModalOpen.value = true
}

const modalClose = () => {

    isModalOpen.value=false
}

const props = defineProps({
    task:{
        type: String,
    },
    

})

</script>
<template>
    <div>
        <a class ="listItem"  @click="openModal">{{props.task}}</a>
        <Modal :open="isModalOpen" @close-modal="modalClose">
            <template #header><h1>{{props.task}}</h1></template>
            <template #body></template>
        </Modal>
        
    </div>
</template>

<style scoped>


</style>