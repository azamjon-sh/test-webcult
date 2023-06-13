<template>
    <header class="header">
        <div class="content">
            <div class="header__inner">
                <div class="header__logo">
                    <img src="src/assets/img/logo-museum.svg" alt="">
                </div>
                <MenuComponent/>
                <div class="header__search">
                    <input class="header__search__input" v-model="search" name="search"
                           placeholder="Поиск по названию картины"
                           @input="$emit('searchText', search)"/>

                    <button class="header__search__btn" @click="$emit('searchText', search)">
                        <span>Найти</span>
                    </button>
                    <div class="header__basket">
                        <img src="src/assets/img/bag-outline.svg" alt="">
                        <span v-if="productCount?.length">{{ productCount.length }}</span>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
<script>

import MenuComponent from "./MenuComponent.vue";

export default {
    name: 'HeaderComponent',
    props: ['productCount'],
    components: {MenuComponent},
    data() {
        return {
            search: ''
        }
    },
}
</script>
