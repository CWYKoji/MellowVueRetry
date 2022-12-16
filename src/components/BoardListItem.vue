<script setup>
import Card from './Card.vue'
import { ref } from 'vue'

const props = defineProps({
    task:{
        type: String,
    },
})

</script>
<template>
        <Card></Card>
</template>

<style scoped>

</style>