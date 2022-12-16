<script setup>
import { ref, reactive } from 'vue';
import List from './List.vue'
import NewListButton from './NewListButton.vue';

const lists = reactive([])

const createList = () => {
    lists.push({
        id: '',
        title: 'New list',
        cards: [],
    })
}

const updateListTitle = (listIndex, newTitle) =>{
    lists[listIndex].title = newTitle
}

const createCard = (listIndex, title) => {
    lists[listIndex].cards.push({
        id: '',
        title: title,
    })
}

const deleteList = (listIndex) =>{
  lists.splice(listIndex,1)
}

const deletecard = (cardIndex, listIndex) =>{
  lists[listIndex].cards.splice(cardIndex,1)
}

const updateCardTitle = (cardIndex, listIndex, newTitle) =>{
  lists[listIndex].cards[cardIndex].title = newTitle
}

const updateCardDescription = (cardIndex, listIndex, newDescription)=>{
  lists[listIndex].cards[cardIndex].content = newDescription
}

</script>




<template>
    <div class = "boardSetup">
        <List
          v-for="(list, index) in lists"
          :list="list" :key="list.id"
          @update-list-title="(title) => updateListTitle(index, title)"
          @create-card="(name) => createCard(index, name)"
          @delete-List="() => deleteList(index)"
          @delete-card="(cardIndex) => deletecard(cardIndex, index)"
          @update-card-title="(cardIndex, newTitle)=> updateCardTitle(cardIndex, index, newTitle)"
          @update-card-description="(cardIndex, newDescription)=> upCardDescription(cardIndex, index, newDescription)"
        ></List>
        <NewListButton
          @create="createList"
        ></NewListButton>
  </div>
</template>


<style scoped>
  .boardSetup{
    position: fixed;
    display: flex;
    top: 83px;
    left: 0px;
    width:100%;
    height: 100%;
    background-color: #add4ff;
  }



</style>