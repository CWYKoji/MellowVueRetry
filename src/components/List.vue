<script setup>
import { ref } from 'vue';
import Card from './Card.vue'
import NewCardButton from './NewCardButton.vue'
import IconDeleteBin from './icons/IconDeleteBin.vue';


const emit = defineEmits(['update-list-title', 'delete-list','update-card-title', 'update-card-description'])

const editing = ref(false)
const listTitleEdit = ref(null)

const props = defineProps({
    list: {
        type: Object,
    }

})

const edit = () =>{
    editing.value = true
}

const saveEdit= () => {
    emit('update-list-title', listTitleEdit.value.value)
    editing.value = false
}

const deleteList=()=>{
    emit('delete-list')
}

</script>

<template>
    <div class="listContainer">
        <div>
            <div class="listHeader">
                <h2 @click="edit">{{editing ? '&nbsp;' : list.title}}</h2>
                <input
                    v-if="editing"
                    type="text"
                    @change="saveEdit"
                    :value="list.title"
                    ref="listTitleEdit"
                />
                <div class="deleteButton" @click="deleteList">
                    <IconDeleteBin />
                </div>
            </div>
            <div>
                <Card
                    v-for="card, index in list.cards"
                    :key="card.id"
                    :card="card"
                    @delete-card="$emit('delete-card', index)"
                    @update-card-title="(title) => $emit('update-card-title', index, title,)"
                    @update-card-description="(description) => $emit('update-card-description', index, description,)"
                ></Card>
                <NewCardButton
                    @create="(name) => $emit('create-card', name)"
                ></NewCardButton>
            </div>
        </div>
    </div>


</template>

<style scoped>

.listContainer{
    height: fit-content;
    width: 175px;
    background-color: #fff;
    flex-direction: column;
    overflow-x: hidden;
    overflow-y: auto;
    margin-left: 10px;
    box-shadow: 
    0 2.8px 2.2px rgba(0,0,0,0.034), 
    0 6.7px 5.3px rgba(0,0,0,0.048),
    0 12.5px 10px rgba(0,0,0,0.06),
    0 22.3px 17.9px rgba(0,0,0,0.072),
    0 41.8px 33.4px rgba(0,0,0,0.086),
    0 100px 80px rgba(0,0,0,0.12);
    border-radius: 3px;
}

.listHeader{
    display: flex;  
    justify-content: space-between;
}

.deleteButton{
    display: flex;   
    align-self: center;
    margin-left: 10px;
}
</style>