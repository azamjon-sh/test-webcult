<template>
    <footer class="footer">
        <div class="content">
            <div class="footer__inner">
                <div class="footer__logo">
                    <img src="src/assets/img/logo-museum.svg" alt="">
                </div>
                <MenuComponent/>
                <div class="footer__contact">
                    <a href="tel:+74959999999" class="footer__phone">
                        <img src="src/assets/img/phone.svg" alt="">
                        <span>+7 (495) 999-99-99</span>
                    </a>
                    <a href="https://yandex.ru/maps/193/voronezh/house/ulitsa_nikitina_119/Z0AYcw5kTUwCQFtrfXR2eHRqZw==/?ll=39.594495%2C51.879893&z=17" class="footer__phone">
                        <img src="src/assets/img/adress.svg" alt="">
                        <span>г. Воронеж, ул. Никитина, 119А</span>
                    </a>
                </div>
            </div>
        </div>
    </footer>
</template>

<script>
import MenuComponent from "./MenuComponent.vue";

export default {
    name: "FooterComponent",
    components: {MenuComponent}
}
</script>

<style scoped>

</style>
