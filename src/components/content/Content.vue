<template>
    <div class="content" :style="themeStyle">
        <AddButton :themeStyle="themeStyle" :handleModal="handleModal" />
        <Board :themeStyle="themeStyle" :cards="cards" :statuses="statuses" :moveCard="moveCard" :handleModal="handleModal" />
    </div>
</template>

<script>
import AddButton from "./AddButton.vue"
import Board from "./board/Board.vue"
export default {
    components: {
        AddButton, Board
    },
    props: {
        themeStyle: Object,
        cards: Object,
        statuses: Object,
        moveCard: Function,
        handleModal: Function
    }
}
</script>

<style scoped>
.content {
    padding: 0 13vw;
    padding-bottom: 22px;
    transition: .4s;
    background-color: var(--content-background);
}

@media (max-width: 992px) {
    .content {
        padding: 0 7vw;
    }
}
</style>