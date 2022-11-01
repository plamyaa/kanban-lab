<template>
  <div class="footer">
    <div class="footer__wrapper">
      <p>Сергеев Михаил 211-321</p>
      <a class="footer__link" href="#">
        <svg
          class="footer__arrow"
          viewBox="0 0 34 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M33.0607 13.0607C33.6464 12.4749 33.6464 11.5251 33.0607 10.9393L23.5147 1.3934C22.9289 0.807612 21.9792 0.807612 21.3934 1.3934C20.8076 1.97918 20.8076 2.92893 21.3934 3.51472L29.8787 12L21.3934 20.4853C20.8076 21.0711 20.8076 22.0208 21.3934 22.6066C21.9792 23.1924 22.9289 23.1924 23.5147 22.6066L33.0607 13.0607ZM0 13.5H32V10.5H0V13.5Z"
          /></svg
      ></a>
    </div>
  </div>
</template>
<script>
export default {
  name: 'AppFooter',
};
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
  height: 34px;
}

.footer__link:visited {
  color: var(--board-text);
}

.footer__arrow {
  padding: 5px;
  box-sizing: content-box;
  width: 20px;
  height: 20px;
  transform: rotate(270deg);
  border: 2px solid var(--main-color);
  border-radius: 5px;
}

.footer__arrow path {
  fill: var(--main-color);
}

@media (min-width: 1441px) {
  .footer__wrapper {
    padding: 0;
  }
}
</style>
