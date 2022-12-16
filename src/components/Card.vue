<script setup>
import { ref } from 'vue';
import Modal from './Modal.vue'

const emit = defineEmits('delete-card', 'update-card-title', 'update-card-description')
const props = defineProps({
    card:{
        type: Object,
    }

})

const modalOpen = ref(false)
const editTitle = ref(false)
const cardTitleEdit = ref(null)
const editDescription = ref(false)
const cardDescriptionEdit = ref(null)

const deleteCard = () =>{
    let reallyDelete = confirm('Are you sure you want to delete this card?')
    if(reallyDelete){
        emit('delete-card')
    }

}



const closeModal = () => {
    modalOpen.value = false
    editTitle.value = false
    editDescription.value = false
}

const saveTitle = () =>{
    
    emit('update-card-title', cardTitleEdit.value.value)
    editTitle.value = false

}

const saveDescription = () =>{
    
    emit('update-card-description', cardDescriptionEdit.value.value)
    editDescription.value = false

}



</script>

<template>
    <div @click="modalOpen = true">
        {{ card.title}}
    </div>
    <Modal v-if="modalOpen" :open="modalOpen" @close="closeModal">
        <template #header>
            <h2 @click="editTitle=true">{{card.title}}</h2>
            <input 
            v-if="editTitle" 
            type="text" 
            :value="card.title" 
            class="titleEdit"
            ref="cardTitleEdit"
            @keypress.enter="saveTitle"
            />
        </template>
        <template #body>
            <div v-if="!editDescription" @click="editDescription = true">{{card.content}}</div>
            
            <textarea v-else="editDescription">{{card.content}}</textarea>
            
        </template>
        <template #footer>
            <button @click="deleteCard">Delete</button>
            <button v-if="editDescription" :value="card.content" ref="cardDescriptionEdit">Save</button>
        </template>
    </Modal>


</template>

<style scoped>

.titleEdit{
    position:absolute;
    width: 90%;
    font-size: 30px;
    background-color: white;
    top: 0;
    left: 0;
    border: none;

}


</style>