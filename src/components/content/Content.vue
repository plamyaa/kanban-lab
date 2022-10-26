<template>
    <div class="content">
        <ContentAddButton :handleModal="handleModal" />
        <Board
            :cards="cards"
            :statuses="statuses"
            :moveCard="moveCard"
            :handleModal="handleModal"
        />
    </div>
</template>

<script>
import ContentAddButton from './ContentAddButton.vue'
import Board from './board/Board.vue'
export default {
    name: 'AppContent',
    components: {
        ContentAddButton,
        Board,
    },
    props: {
        cards: Object,
        statuses: Object,
        moveCard: Function,
        handleModal: Function,
    },
}
</script>

<style scoped>
.content {
    display: grid;
    padding: 0 13vw;
    padding-bottom: 22px;
    transition: 0.4s;
    background-color: var(--content-background);
    max-width: 1440px;
    width: 100%;
    margin: auto;
}

@media (max-width: 992px) {
    .content {
        padding: 0 7vw;
    }
}
@media (min-width: 1440.01px) {
    .content {
        padding: 0;
        padding-bottom: 15px;
    }
}
</style>
