<template>
    <section class="intro">
        <div class="content">
            <h1 class="intro__title">
                Картины эпохи Возрождения
            </h1>
            <div class="intro__list">
                <div class="intro__item" v-for="(item,index) in items" :key="index">
                    <img :src="item.imgUrl" alt="" class="intro__image">
                    <div class="intro__body"><h3 class="intro__name">
                        {{ item.title }}
                    </h3>
                        <div class="intro__bottom" v-if="!item.sold">
                            <div class="intro__price">
                                <span class="price-old" v-if="item.oldPrice">{{ item.oldPrice }}</span>
                                {{ item.price }}
                            </div>
                            <button class="intro__buy"
                                    @click.prevent="addToBasket(item.id)"
                                    :class="{'added' : storageItems.indexOf(item.id) >= 0}">
                                <img src="src/assets/img/feather_check.svg" alt=""
                                     v-if="!loading[item.id] && storageItems.indexOf(item.id) >= 0" class="check">
                                <span v-if="!loading[item.id]">
                                    {{ storageItems.indexOf(item.id) >= 0 ? 'В корзине' : 'Купить' }}
                                </span>
                                <img v-if="loading[item.id]" src="src/assets/img/spener.gif" alt="">
                            </button>

                        </div>
                        <div v-else class="intro__sold">
                            Продана на аукционе
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
export default {
    name: "IntroComponent",
    props: {
        items: Array,
    },
    data() {
        return {
            storageItems: [],
            loading: [],
        }
    },
    methods: {
        async addToBasket(id) {
            this.loading[id] = true
            let request = await fetch('https://jsonplaceholder.typicode.com/posts/1')
            if (request.status === 200) {
                let items = JSON.parse(localStorage.getItem('products')) || []
                if (items.indexOf(id) < 0) {
                    items.push(id)
                    alert('Успешно добавлено в корзину')
                } else {
                    let index = items.indexOf(id);
                    items.splice(index, 1);
                    alert('Убрано из корзины')
                }
                localStorage.setItem('products', JSON.stringify(items))
                this.storageItems = items
                this.$emit('addToBasket')
                this.loading[id] = false

            } else {
                alert('Что-то пошло не так')
                this.loading[id] = false
            }
        },
    },
    mounted() {
        this.storageItems = JSON.parse(localStorage.getItem('products'))
    },
}
</script>

<style scoped>

</style>
