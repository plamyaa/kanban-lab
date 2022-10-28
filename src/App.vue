<template>
    <div class="app__wrapper" :style="themeStyle">
        <Header :theme="theme" :changeTheme="() => (theme = !theme)" />
        <Content
            :cards="cards"
            :statuses="statuses"
            :moveCard="moveCard"
            :handleModal="handleModal"
        />
        <Footer />
    </div>
</template>

<script>
import Header from '@/components/header/Header.vue'
import Content from '@/components/content/Content.vue'
import Footer from '@/components/footer/Footer.vue'

export default {
    name: 'App',
    components: {
        Header,
        Content,
        Footer,
    },
    data() {
        return {
            cards: [
                {
                    id: 1,
                    task: 'lorem',
                    data: new Date(2011, 6, 13),
                    priority: 1,
                },
                {
                    id: 2,
                    task: 'lorem impu',
                    data: new Date(2022, 8, 1),
                    priority: 2,
                },
                {
                    id: 3,
                    task: 'lorem impus uiabl',
                    data: new Date(2022, 10, 26),
                    priority: 3,
                },
            ],
            statuses: {
                plan: [1],
                atWork: [2],
                ready: [3],
            },
            theme: false,
        }
    },
    methods: {
        moveCard(id, direction) {
            let statusIndex
            const keys = Object.keys(this.statuses)
            keys.forEach((status, index) => {
                const statusArray = Object.values(this.statuses[status])
                if (statusArray.includes(id)) {
                    this.statuses[status] = statusArray.filter(
                        (statusId) => statusId !== id
                    )
                    statusIndex = index + direction
                }
            })
            if (statusIndex === Object.keys(this.statuses).length) {
                // archive card
                return
            }
            this.statuses[keys[statusIndex]].push(id)
        },
        handleModal(task, priority, cardId) {
            switch (cardId) {
                case 0:
                    let newId = 0
                    this.cards.map((obj) => {
                        if (obj.id > newId) {
                            newId = obj.id
                        }
                    })
                    this.statuses.plan.push(newId + 1)
                    this.cards.push({
                        id: newId + 1,
                        task: task,
                        data: new Date(),
                        priority: priority,
                    })
                default:
                    this.cards = this.cards.map((card) => {
                        if (card.id === cardId) {
                            card.task = task
                            card.priority = priority
                        }
                        return card
                    })
            }
        },
    },
    computed: {
        themeStyle() {
            switch (this.theme) {
                case true:
                    return {
                        '--main-color': '#33417C',
                        '--secondary-color': '#585858',
                        '--main-color__text': '#ECECEC',
                        '--switcher-background-color': '#0B1340',
                        '--content-background': '#323332',
                        '--board-text': '#ECECEC',
                    }
                default:
                    return {
                        '--main-color': '#2599FB',
                        '--secondary-color': '#F2F9FF',
                        '--main-color__text': '#FFFFFF',
                        '--switcher-background-color': '#BBE0FD',
                        '--content-background': '#FFFFFF',
                        '--board-text': '#2599FB',
                    }
            }
        },
    },
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    border: 0;
}

.button {
    cursor: pointer;
}

.app__wrapper {
    display: grid;
    grid-template-rows: auto 1fr auto;
    height: 100vh;
    transition: 0.4s;
    background: var(--content-background);
}
</style>
