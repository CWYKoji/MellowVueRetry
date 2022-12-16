<script setup>
import IconClose from './icons/IconXCircle.vue'
import { ref } from 'vue';

const modalDescription = ref('')
const emit = defineEmits(['close-modal'])
const props = defineProps ({

    open:{
        type: Boolean,
        default: false
    }
})

const close = () =>{
    emit('close-modal')
}

</script>


<template>
    <div v-if="open" class="modal-background" @click.self="$emit('close')">
        <div class="modal">
            <div class="modal-heading">
                <slot name="header"></slot>
                <IconClose @click="$emit('close')" />
            </div>
            <div class="modal-body">
                <slot name="body">
                <textarea  v-model="modalDescription"></textarea>
                </slot>
            </div>
            <div class="modal-footer">
                <slot name="footer"></slot>
            </div>
        </div>
    </div>

</template>

<style scoped>

.modal-heading{
    position: relative;
    display: flex;
    align-items: center;
    justify-content: space-between;

}
.modal-background{
    background: rgba(0,0,0,.5);
    width: 100%;
    height: 100vh;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 50;
    display: flex;
    justify-content: center;
}
.modal{
    background: white;
    padding: 10px;
    color: black;
    margin-top: 100px;
    width: 600px;
    height: fit-content;
}


.modal-heading{
    margin: 1rem;
    padding-bottom: 0.5rem;

}

.modal-body{
    margin: 1rem;
    padding-bottom: 0.5rem;

}


</style>