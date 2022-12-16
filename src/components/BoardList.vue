<script setup>
import { onMounted, ref } from 'vue';
import BoardListItem from './BoardListItem.vue'
import IconNewFile from './icons/IconNewFile.vue'
import axios from 'axios'

const baseUrl = 'http://localhost/api'

onMounted(() => {
    loadListFromApi()
})

const loadListFromApi = () => {
    axios.get(`${baseUrl}/todo-lists`)
    .then((response) => {
        const data = response.data.data
        alert(response.data.title)
        listItems.value = data
    })

}

const listItems = ref([])
const todo = ref('')

const addToList= () =>{

    listItems.push({
        task: 1,
        
    })

    todo.value = ''
    
}

</script>

<template>
    <div class = "cardsComponents">
        <div class = "cardsArray">
            <BoardListItem v-for="item in listItems"></BoardListItem>
        </div>
        <div class="taskContainer">  
            <button class="butAddList" type="button" @click="addToList" > 
                Add Card
                <IconNewFile/>
            </button>
        </div>
    </div>
   
    
    
</template>

<style scoped>



.newTaskTitle{
    width: 100%;

}
.butAddList{
  display: flex;   
  align-self: center;
  margin-left: 10px;
}

.cardsArray{
    display: flex;
}
.cardsComponents{
    display: flex;
}



</style>