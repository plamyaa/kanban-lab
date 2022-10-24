<template>
    <header :style="themeStyle">
        <img src="../../../public/logo-black.png" alt="" class="header__image"/>
        <h1 class="header__name">Kanban Board</h1>
        <ColorSwitcher :theme="theme" :themeStyle="themeStyle" :changeTheme="changeTheme"/>
    </header>
</template>

<script>
import ColorSwitcher from "@/components/header/ColorSwitcher.vue"
export default {
    props: {
        theme: Boolean,
        changeTheme: Function,
        themeStyle: Object
    },
    components: {
            ColorSwitcher
        }
    }
</script>

<style scoped>
    header {
        transition: .4s;
        height: 70px;
        width: 100%;
        display: flex;
        background-color: var(--main-color);
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
</style>