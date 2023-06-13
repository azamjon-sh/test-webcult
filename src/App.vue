<template>
    <HeaderComponent :productCount="products" @searchText="doFilter"/>
    <main>
        <IntroComponent @addToBasket="getBasket" :items="filtered != null ? filtered : itemList"/>
    </main>
    <FooterComponent/>
</template>
<script>
import {defineComponent} from "vue";
import HeaderComponent from "./components/HeaderComponent.vue";
import IntroComponent from "./components/IntroComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";

export default defineComponent({
    components: {IntroComponent, HeaderComponent, FooterComponent},
    data() {
        return {
            products: [],
            itemList: [
                {
                    imgUrl: 'src/assets/img/1.png',
                    id: 1,
                    sold: false,
                    title: '«Рождение Венеры» Сандро Боттичелли',
                    price: '1 000 000 $',
                    oldPrice: '2 000 000 $'
                },
                {
                    imgUrl: 'src/assets/img/2.png',
                    id: 2,
                    sold: false,
                    title: '«Тайная вечеря»  Леонардо да Винчи',
                    price: '3 000 000 $'
                },
                {
                    imgUrl: 'src/assets/img/3.png',
                    id: 3,
                    title: '«Сотворение Адама» Микеланджело',
                    sold: false,
                    price: '6 000 000 $',
                    oldPrice: '5 000 000 $'
                },
                {
                    imgUrl: 'src/assets/img/4.png',
                    id: 4,
                    title: '«Урок анатомии»  Рембрандт',
                    sold: true,
                },
            ],
            filtered: null,
        }
    },
    methods: {
        getBasket() {
            this.products = JSON.parse(localStorage.getItem('products'))
        },
        doFilter(val) {
            console.log(val)
            this.filtered = this.itemList.filter(el => el.title.toLowerCase().includes(val.toLowerCase()))
            if (val == '') {
                this.filtered = null
            }
        }
    },
    mounted() {
        this.getBasket()
    },
})
</script>
