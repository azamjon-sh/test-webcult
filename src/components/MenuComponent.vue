<template>
    <div class="header__menu">
        <a :href="item.url" class="header__item" v-for="item in menu">
            {{ item.title }}
        </a>
    </div>
</template>

<script>
export default {
    name: "MenuComponent",
    data() {
        return {
            menu: [
                {
                    url: '#',
                    title: 'Каталог'
                },
                {
                    url: '#',
                    title: 'Доставка'
                },
                {
                    url: '#',
                    title: 'Оплата'
                },
                {
                    url: '#',
                    title: 'Контакты'
                },
                {
                    url: '#',
                    title: 'О галерее'
                },
            ]
        }
    }
}
</script>

<style scoped>

</style>
