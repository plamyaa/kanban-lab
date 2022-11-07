<template>
  <div class="card" :id="card.id" draggable="true" @dragstart="onDragging">
    <div class="card__header">
      <h3 class="card__number">Задача: {{ card.id }}</h3>
      <span class="card__priority" :class="cardPriority">{{
        card.priority
      }}</span>
    </div>
    <p class="card__task">{{ card.task }}</p>
    <p class="card__date">{{ formateDate(card.data) }}</p>
    <CardButtons
      :handleModal="handleModal"
      :status="status"
      :cardId="card.id"
      :moveCard="moveCard"
      :cardTask="card.task"
      :cardPriority="card.priority"
    />
  </div>
</template>

<script>
import CardButtons from './СardButtons.vue';
export default {
  name: 'BoardCard',
  props: {
    card: Object,
    moveCard: Function,
    handleModal: Function,
    status: String,
    drag: Function,
  },
  components: {
    CardButtons,
  },
  methods: {
    onDragging(event) {
      event.dataTransfer.setData('itemId', event.target.id);
      event.dataTransfer.setData('boardId', event.target.parentNode.id);
    },
    formateDate(date) {
      const year = date.getFullYear();
      const month = date.getMonth() + 1;
      const _date = date.getDate();
      const time = String(date).slice(16, 25);
      const formatted = `${
        _date.toString().length === 1 ? '0' + _date : _date
      }.${month.toString().length === 1 ? '0' + month : month}.${year} ${time}`;
      return formatted;
    },
  },
  computed: {
    cardPriority() {
      return 'card__priority_' + String(this.card.priority);
    },
  },
};
</script>

<style scoped>
.card {
  transition: 0.4s;
  width: 100%;
  border: 2px solid var(--main-color);
  border-radius: 5px;
  padding: 8px 13px;
  background-color: var(--content-background);
  color: var(--board-text);
  max-width: 235px;
}

.card__header {
  display: flex;
  justify-content: space-between;
}

.card__number {
  margin-bottom: 15px;
}

.card__priority {
  width: 22px;
  height: 22px;
  border: 1px solid var(--main-color);
  border-radius: 100%;
  text-align: center;
  line-height: 20px;
  transition: 0.4s;
  color: var(--main-color);
}

.card__priority_1 {
  background-color: #fea3a2;
}

.card__priority_2 {
  background-color: #fffc9e;
}

.card__priority_3 {
  background-color: #adecc7;
}

.card__task {
  margin-bottom: 10px;
  word-wrap: break-word;
}
</style>
