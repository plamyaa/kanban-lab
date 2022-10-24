<template>
    <div class="footer" :style="themeStyle">
        <p>Сергеев Михаил 211-321</p>
        <a class="footer__link" href="#">Cсылка</a>
    </div>
</template>

<script>
export default {    
    props: {
        themeStyle: Object,
    }
}
</script>

<style scoped>
.footer {
    width: 100%;
    height: 45px;
    background-color: var(--secondary-color);
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 9vw;
    color: var(--board-text);
    transition: .4s;
}

.footer__link {
    text-decoration: none;
}
.footer__link:visited {
    color: var(--board-text);
}
</style>