<template>
    <button :style="themeStyle" @click="showModal = true">Создать задачу</button>
    <ModalWindow v-if="showModal" :closeModal="() => showModal = false" task="" priority="1" id="0"
        :handleModal="handleModal" :themeStyle="themeStyle"/>
</template>

<script>
import ModalWindow from "@/components/modalWindow/ModalWindow.vue"
export default {
    components: {
        ModalWindow
    },
    props: {
        themeStyle: Object,
        handleModal: Function,
    },
    data() {
        return {
            showModal: false
        }
    },
}
</script>

<style scoped>
button {
    border-radius: 5px;
    margin-top: 50px;
    width: 150px;
    height: 40px;
    background-color: var(--main-color);
    color: var(--main-color__text);
}

.button_dark {
    background-color: #33417C;
    color: #ECECEC;
}
</style>