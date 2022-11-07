<template>
  <div class="card__buttons">
    <button
      class="button card__back"
      :disabled="status === 'План'"
      @click="moveCard(cardId, -1)"
    >
      <svg
        class="button__left-arrow"
        viewBox="0 0 34 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M33.0607 13.0607C33.6464 12.4749 33.6464 11.5251 33.0607 10.9393L23.5147 1.3934C22.9289 0.807612 21.9792 0.807612 21.3934 1.3934C20.8076 1.97918 20.8076 2.92893 21.3934 3.51472L29.8787 12L21.3934 20.4853C20.8076 21.0711 20.8076 22.0208 21.3934 22.6066C21.9792 23.1924 22.9289 23.1924 23.5147 22.6066L33.0607 13.0607ZM0 13.5H32V10.5H0V13.5Z"
        />
      </svg>
    </button>
    <button class="button card__edit" @click="showModal = true">Edit</button>
    <button class="button card__next" @click="moveCard(cardId, 1)">
      <span v-if="status === 'Готово'">X</span>
      <svg
        v-else
        class="button__right-arrow"
        viewBox="0 0 34 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M33.0607 13.0607C33.6464 12.4749 33.6464 11.5251 33.0607 10.9393L23.5147 1.3934C22.9289 0.807612 21.9792 0.807612 21.3934 1.3934C20.8076 1.97918 20.8076 2.92893 21.3934 3.51472L29.8787 12L21.3934 20.4853C20.8076 21.0711 20.8076 22.0208 21.3934 22.6066C21.9792 23.1924 22.9289 23.1924 23.5147 22.6066L33.0607 13.0607ZM0 13.5H32V10.5H0V13.5Z"
        />
      </svg>
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
