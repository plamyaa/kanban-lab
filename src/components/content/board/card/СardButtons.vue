<template>
    <div class="card__buttons" :style="themeStyle">
        <button 
            class="card__back" 
            :disabled="status === 'План'" 
            @click="moveCard(cardId, -1)">
            &lt;-
        </button>
        <button 
            class="card__edit" 
            @click="showModal = true">
            Edit
        </button>
        <button 
            class="card__next" 
            @click="moveCard(cardId, 1)">
            {{status === "Готово" ? "X" : "->"}}
        </button>
    </div>
    <ModalWindow 
        v-if="showModal" 
        :closeModal="() => showModal = false" 
        :id="cardId"
        :task="cardTask" 
        :priority="cardPriority" 
        :handleModal="handleModal" 
        :themeStyle="themeStyle"/>

</template>

<script>
import ModalWindow from "@/components/modalWindow/ModalWindow.vue";
export default {
    data() {
        return {
            showModal: false,
            nextButtonValue: "->",
        }
    },
    props: {
        handleModal: Function,
        cardId: Number,
        themeStyle: Object,
        status: String,
        moveCard: Function,
        cardTask: String,
        cardPriority: Number,
    },
    components: {
        ModalWindow,
    },
    methods: {
        handleMove(direction) {

            moveCard(this.cardId, direction);
        }
    }
}
</script>

<style scoped>
.card__buttons {
    display: flex;
    justify-content: space-between;
}

.card__back, .card__edit, .card__next {
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
</style>