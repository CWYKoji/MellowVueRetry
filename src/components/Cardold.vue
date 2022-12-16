<script setup>
  import { ref } from 'vue';
  import TDList from './TDList.vue'

  const title = ref('')
</script>

<template>
  <form>
    <div class="card">
      <div class="cardTitle">
        <input class="inputCardTitle" placeholder="Title" type="text" name="title" v-on:keydown.enter.prevent/>
      </div>
        <div class ="cardContents">
          <TDList></TDList>
        </div>
    </div>
  </form>
</template>

<style scoped>

.card{
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


.cardContents{
  width: 100%;
}

.inputCardTitle{
  width: 100%;
  height: 25px;
  border-style:hidden; 
}

.inputCardContents{
  width: 100%;
  height: 120px;
  border-style: hidden;
  
}

</style>