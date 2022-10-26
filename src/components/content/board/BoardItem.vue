<template>
    <div class="board__item" :id="boardId" @drop="drop" @dragover="allowDrop">
        <h2 class="item__header">
            {{ statusesName[boardId] }} ({{ cards.length }})
        </h2>
        <Card
            v-for="card in cards"
            :key="card.id"
            :card="card"
            :status="statusesName[boardId]"
            :moveCard="moveCard"
            :handleModal="handleModal"
        />
    </div>
</template>

<script>
import Card from './card/Card.vue'
export default {
    name: "BoardItem",
    data() {
        return {
            statusesName: ['План', 'В работе', 'Готово'],
        }
    },
    props: {
        cards: Object,
        moveCard: Function,
        handleModal: Function,
        boardId: Number,
    },
    components: {
        Card,
    },
    methods: {
        allowDrop(event) {
            event.preventDefault()
        },
        drop(event) {
            event.preventDefault()
            const cardId = +event.dataTransfer.getData('itemId')
            const oldBoardId = +event.dataTransfer.getData('boardId')
            const direction = +this.boardId - oldBoardId
            if (direction === 0) return
            this.moveCard(cardId, direction)
        },
    },
}
</script>

<style scoped>
.board__item {
    transition: 0.4s;
    width: 100%;
    background-color: var(--secondary-color);
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px 10px;
    gap: 15px;
    min-height: 490px;
}

.item__header {
    transition: 0.4s;
    color: var(--board-text);
    font-size: 20px;
    margin-bottom: 10px;
}
</style>
