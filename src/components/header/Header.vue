<template>
    <header class="header">
        <div class="header__wrapper">
            <img
                src="../../../public/logo-black.png"
                alt=""
                class="header__image"
            />
            <h1 class="header__name">Kanban Board</h1>
            <ColorSwitcher :theme="theme" :changeTheme="changeTheme" />
        </div>
    </header>
</template>

<script>
import ColorSwitcher from '@/components/header/HeaderColorSwitcher.vue'
export default {
    name: 'AppHeader',
    props: {
        theme: Boolean,
        changeTheme: Function,
        themeStyle: Object,
    },
    components: {
        ColorSwitcher,
    },
}
</script>

<style scoped>
.header {
    background-color: var(--main-color);
}

.header__wrapper {
    max-width: 1440px;
    margin: auto;
    transition: 0.4s;
    height: 70px;
    width: 100%;
    display: flex;
    align-items: center;
    padding: 0 9vw;
    color: var(--main-color__text);
    justify-content: space-between;
}

.header__image {
    width: 90px;
    height: 90px;
}

.header__name {
    margin-left: 10%;
}

@media (min-width: 1440.01px) {
    .header__wrapper {
        padding: 0;
    }
}
</style>
