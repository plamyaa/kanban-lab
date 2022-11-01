<template>
  <div class="board">
    <BoardItem
      v-for="(status, key, index) in statuses"
      :key="index"
      :cards="getFilteredCards(cards, status)"
      :moveCard="moveCard"
      :handleModal="handleModal"
      :boardId="index"
    />
  </div>
</template>

<script>
import BoardItem from './BoardItem.vue';
export default {
  name: 'ContentBoard',
  components: {
    BoardItem,
  },
  props: {
    cards: Object,
    statuses: Object,
    moveCard: Function,
    handleModal: Function,
  },
  methods: {
    getFilteredCards(cards, ids) {
      return cards.filter((card) => ids.includes(card.id));
    },
  },
};
</script>

<style scoped>
.board {
  margin-top: 20px;
  width: 100%;
  display: flex;
  gap: 20px;
}

@media (max-width: 762px) {
  .board {
    flex-direction: column;
  }
}
</style>
