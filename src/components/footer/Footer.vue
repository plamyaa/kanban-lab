<template>
    <div class="footer">
        <div class="footer__wrapper">
            <p>Сергеев Михаил 211-321</p>
            <a class="footer__link" href="#">Наверх</a>
        </div>
    </div>
</template>
<script>
export default {
    name: 'AppFooter',
}
</script>
<style scoped>
.footer {
    background-color: var(--secondary-color);
}

.footer__wrapper {
    max-width: 1440px;
    margin: auto;
    width: 100%;
    height: 45px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 9vw;
    color: var(--board-text);
    transition: 0.4s;
}

.footer__link {
    text-decoration: none;
}

.footer__link:visited {
    color: var(--board-text);
}

@media (min-width: 1440.01px) {
    .footer__wrapper {
        padding: 0;
    }
}
</style>
