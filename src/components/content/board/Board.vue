<template>
    <div class="board">
        <BoardItem 
            v-for="(status, key, index) in statuses" 
            :themeStyle="themeStyle" 
            :cards="getFilteredCards(cards, status)"
            :moveCard="moveCard" 
            :handleModal="handleModal" 
            :boardId="index" />
    </div>
</template>

<script>
import BoardItem from "./BoardItem.vue"
export default {
    components: {
        BoardItem,
    },
    props: {
        themeStyle: Object,
        cards: Object,
        statuses: Object,
        moveCard: Function,
        handleModal: Function
    },
    methods: {
        getFilteredCards(cards, ids) {
            return cards.filter(card => ids.includes(card.id));
        },
    },
}
</script>

<style scoped>
.board {
    margin-top: 20px;
    width: 100%;
    display: flex;
    gap: 20px;
}
</style>