<template>
    <div class="map">
        <div class="map__header">
            <div class="map__menu">
                <span class="map__menu--title" @click="toggleMenu = !toggleMenu">Офисы Softline <i><img :src="require('@/assets/svgs/arrow-up.svg')" alt=""></i></span>
                <div class="map__menu--items" v-if="toggleMenu">
                    <ul class="map__list" v-for="(place, i) in places" :key="i">
                        <li class="map__list--groupname">{{ place.name }}</li>
                        <li class="map__list--subname" v-for="(item, j) in place.children" :key="j">
                            {{ item.name }}
                        </li>
                    </ul>

                </div>
            </div>

            <ul class="map-menu-list">
                <li class="map-menu-list__item active">Все</li>
                <li v-for="(item, i) in places" :key="i"> {{ item.name }} </li>
            </ul>
        </div>
        <div class="map__body">
            <map name="map">
                <img :src="require('@/assets/images/map.jpg')" alt="">
            </map>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
    setup() {
        const places = ref([
            {
                name: "Москва",
                children: []
            },
            {
                name: "Центр",
                children: [
                    { name: "Воронеж" },
                    { name: "Ярославль" },
                    { name: "Белгород" }
                ]
            },
            {
                name: "Северо-Запад",
                children: [
                    { name: "Санкт-Петербург" },
                    { name: "Калининградд" }
                ]
            },
            {
                name: "Юг",
                children: [
                    { name: "Ростов-на-Дону" },
                    { name: "Краснодар" },
                    { name: "Волгоград" }
                ]
            },
            {
                name: "Волга",
                children: [
                    { name: "Казань" },
                    { name: "Самара" },
                    { name: "Уфа" },
                    { name: "Оренбург" },
                    { name: "Нижний Новгород" }
                ]
            },
            {
                name: "Урал",
                children: [
                    { name: "Екатеринбург" },
                    { name: "Челябинск" },
                    { name: "Пермь" },
                    { name: "Сургут" },
                    { name: "Тюмень" },
                    { name: "Ижевск" }
                ]
            },
            {
                name: "Сибирь",
                children: [
                    { name: "Новосибирск " },
                    { name: "Омск" },
                    { name: "Томск " },
                    { name: "Красноярск" },
                    { name: "Иркутск" }
                ]
            },
            {
                name: "Дальний Восток",
                children: [
                    { name: "Хабаровск" },
                    { name: "Владивосток" }
                ]
            }
        ]);
        const toggleMenu = ref(false);
        return {
            places,
            toggleMenu
        };
    },
})
</script>


<style lang="scss" scoped>
    $red: #A30C33;
    .map {
        &__header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 3rem;
            width: 100%;
            overflow-x: scroll;
            &::-webkit-scrollbar {
                display: none;
            }
        }
        &-menu-list {
            display: flex;
            align-items: center;
            gap: 3rem;
            font-weight: 600;
            font-size: 1.8rem;
            line-height: 2rem;
           
            .active {
                color: $red;
                border-bottom: .2rem solid $red;
            }
        }
        &__menu {
            display: inline-block;
            position: relative;
            &--title {
                font-weight: 600;
                font-size: 2.4rem;
                line-height: 100%;
            }

            &--items {
                width: 124rem;
                background: #FFFFFF;
                box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.06);
                position: absolute;
                left: 0;
                top: 3rem;
                display: flex;
                gap: 3rem;
                z-index: 10;
            }
        }

        &__list {
            &--groupname {
                font-weight: 600;
                font-size: 1.8rem;
                line-height: 2rem;
                margin: 1rem;       
            }

            &--subname {
                margin: .6rem 1rem;
                font-weight: 400;
                font-size: 18px;
                line-height: 20px;
            }
        }   

        &__body {
            width: 100%;
            height: 100%;
            text-align: left;
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
    }

    @media screen and (max-width: 36rem) {
        .map {
            &__header {
                padding: 1.8rem .5rem;
                flex-direction: column;
                align-items: flex-start;
            }

            &__menu {
                &--title {
                    font-size: 2rem;
                }
                
                &--items {
                    width: 34rem;
                    flex-wrap: wrap;
                    height: 40rem;
                    overflow-x: scroll;
                }
            }

            &-menu-list {
                font-size: 1.4rem;
                gap: 1.6rem;
                margin-top: 2rem;
                width: max-content;
                li {
                    max-width: max-content;
                }
            }

            &__list {

            }
        }
    }
</style>