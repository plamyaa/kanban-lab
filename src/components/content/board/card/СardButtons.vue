<template>
  <div class="card__buttons">
    <button
      class="button card__back"
      :disabled="status === 'План'"
      @click="moveCard(cardId, -1)"
    >
      <CardButtonsArrow :rotate="180" />
    </button>
    <button class="button card__edit" @click="showModal = true">Edit</button>
    <button class="button card__next" @click="moveCard(cardId, 1)">
      <span v-if="status === 'Готово'">X</span>
      <CardButtonsArrow v-else :rotate="0" />
    </button>
  </div>
  <ModalWindow
    v-if="showModal"
    :closeModal="() => (showModal = false)"
    :id="cardId"
    :task="cardTask"
    :priority="cardPriority"
    :handleModal="handleModal"
  />
</template>

<script>
import ModalWindow from '@/components/modalWindow/ModalWindow.vue';
import CardButtonsArrow from './CardButtonsArrow.vue';
export default {
  name: 'CardButtons',
  data() {
    return {
      showModal: false,
      nextButtonValue: '->',
    };
  },
  props: {
    handleModal: Function,
    cardId: Number,
    status: String,
    moveCard: Function,
    cardTask: String,
    cardPriority: Number,
  },
  components: {
    ModalWindow,
    CardButtonsArrow
},
};
</script>

<style scoped>
.card__buttons {
  display: flex;
  justify-content: space-between;
}

.card__back,
.card__edit,
.card__next {
  color: var(--main-color);
  margin-top: 10px;
  border: 2px solid var(--main-color);
  border-radius: 5px;
  padding: 5px;
  background-color: var(--secondary-color);
}

.card__back:disabled,
.card__edit:disabled,
.card__next:disabled {
  opacity: 0.4;
  cursor: auto;
}
.button {
  transition: 0.4s;
  display: flex;
}

.button__left-arrow {
  width: 17px;
  height: 15px;
  transform: rotate(180deg);
}
.button__left-arrow path,
.button__right-arrow path {
  fill: var(--main-color);
}
.button__right-arrow {
  width: 17px;
  height: 15px;
}
</style>
