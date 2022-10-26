<template>
    <modal>
        <div class="modal-mask">
            <div class="modal-wrapper">
                <div class="modal-container">
                    <button class="modal-exit" @click="closeModal">X</button>
                    <form class="modal-form" @submit.prevent>
                        Описание
                        <input
                            v-bind:value="card.task"
                            @input="card.task = $event.target.value"
                            class="modal-task-input"
                            input="text"
                        />
                        Приоритет
                        <select
                            v-model="card.priority"
                            class="modal-task-input"
                            placeholder="Значимость"
                        >
                            <option>1</option>
                            <option>2</option>
                            <option>3</option>
                        </select>
                    </form>
                    <button class="modal-button" @click="onClick">OK</button>
                </div>
            </div>
        </div>
    </modal>
</template>

<script>
export default {
    name: "ModalWindow",
    props: {
        task: String,
        priority: Number,
        id: Number,
        handleModal: Function,
        closeModal: Function,
    },
    data() {
        return {
            card: {
                task: this.task,
                priority: this.priority,
                id: Number(this.id),
            },
        }
    },
    methods: {
        onClick() {
            this.closeModal()
            this.handleModal(this.card.task, this.card.priority, this.card.id)
        },
    },
}
</script>

<style scoped>
.modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #00000080;
    display: table;
    transition: opacity 0.3s ease;
}

.modal-wrapper {
    display: table-cell;
    vertical-align: middle;
}

.modal-container {
    width: 390px;
    margin: 0px auto;
    padding: 40px 60px;
    background-color: var(--content-background);
    border-radius: 2px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
    transition: all 0.3s ease;
    font-family: Helvetica, Arial, sans-serif;
}

.modal-header h3 {
    margin-top: 0;
    color: #42b983;
}

.modal-exit {
    float: right;
    width: 22px;
    height: 22px;
    border: 1px solid var(--main-color);
    border-radius: 100%;
    text-align: center;
    line-height: 20px;
    transition: 0.4s;
    background-color: var(--secondary-color);
    color: var(--main-color);
}

.modal-task-input {
    margin: 10px 0;
    height: 50px;
    width: 100%;
    border: 2px solid var(--main-color);
    color: var(--board-text);
    background-color: var(--secondary-color);
    border-radius: 5px;
    padding: 0 10px;
}

.modal-form {
    font-size: 14px;
    margin-top: 25px;
    color: var(--board-text);
}

.modal-button {
    display: block;
    margin: 30px auto 0;
    height: 40px;
    width: 100px;
    border: 1px solid var(--main-color);
    border-radius: 5px;
    text-align: center;
    line-height: 20px;
    transition: 0.4s;
    background-color: var(--main-color);
    color: var(--main-color__text);
}

.modal .modal-enter .modal-container,
.modal-leave-active .modal-container {
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
}
</style>
