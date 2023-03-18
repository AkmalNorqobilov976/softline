<template>
    <nav class="navbar">
        <a href="#" class="navbar__logo">
            <img :src="require('@/assets/images/logo.png')" alt="">
        </a>
        <ul class="navbar__links">
            <li>
                <router-link class="navbar__link" to="#">
                    Облачные решения
                </router-link>
            </li>
            <li>
                <router-link to="#" class="navbar__link">
                    Кибербезопасность
                </router-link>
            </li>
            <li>
                <router-link to="#" class="navbar__link">
                    Импортозамещение
                </router-link>
            </li>
            <li>
                <router-link to="#" class="navbar__link">
                    Цифровая трансформация
                </router-link>
            </li>
        </ul>
    </nav>
    <header class="header">
        <h1 class="header__title">
            Поставщик услуг цифровой трансформации и кибербезопасности
        </h1>
        <button class="header__btn">Наш сайт</button>
        <div class="header__img">
            <img :src="require('@/assets/images/header.jpg')" alt="">
        </div>
    </header>
</template>


<script lang="ts">
import gsap, { Elastic } from 'gsap'
import { defineComponent, onMounted } from 'vue'

export default defineComponent({
    setup() {
        onMounted(() => {
            gsap.from('.header__title', {
                x: -199,
                y: 299,
                opacity: .4
            });

            gsap.from('.header__btn', {
                y: 100,
                ease: Elastic.easeInOut,
                duration: 1
            })
        })
    }
})
</script>
<style lang="scss" scoped>
    $black: #444444;
    $btn-color: #B01736;
    .navbar {
        display: flex;
        justify-content: space-around;
        align-items: center;
        padding: 3rem 0;
        &__links {
            display: flex;
            align-items: center;
            gap: 2rem;
        }

        &__link {
            font-size: 1.8rem;
            line-height: 2rem;
            font-weight: 600;
            color: $black;
        }
    }
    .header {
        height: auto;
        position: relative;
        padding: 16rem 7rem;
        &__title {
            font-weight: 600;
            font-size: 5.6rem;
            line-height: 100%;
            margin-right: 40rem;
            margin-bottom: 6rem;
        }

        &__btn {
            background: $btn-color;
            color: white;
            border-radius: .8rem;
            border: none;
            outline: none;
            padding: 1.8rem 2.8rem;
        }

        &__img {
            position: absolute;
            top: 0;
            left: 0;
            z-index: -1;
            
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
    }


    @media screen and (max-width: 36rem) {
     .navbar {
        padding: 1.6rem 0;
        flex-direction: column;
        font-size: 1.4rem;
        &__logo {
            text-align: left;
            align-self: self-start;
            margin-bottom: 1.6rem;
        }
        &__links {
            align-self: self-start;
            display: grid;
            grid-template-columns: min-content max-content;
            gap: 1rem;
        }

        &__link {
            line-height: 1.6rem;
            font-size: 1.4rem;
            max-width: min-content;
        }
     }   

     .header {
        padding: 4rem .5rem;
        &__title {
            font-size: 2.8rem;
            margin-bottom: 2.65rem;
            
        }

        &__btn {
            font-size: 1.6rem;
            padding: .65rem 2.55rem;
            line-height: 100%;
        }
        &__img {
            width: 100%;
            height: 30rem;
            
        }
     }
    }
</style>