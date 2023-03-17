<template>
    <div class="card">
        <div class="card__img">
            <img :src="img" alt="" />
        </div>
        <div class="card__info">
            <p class="card__info--title">{{ title }}</p>
            <p class="card__info--description">{{ description }}</p>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";


export default defineComponent({
   props: {
    img: {
        type: String
    },
    title: {
        type: String
    },
    description: {
        type: String
    }
   } 
});
</script>

<style lang="scss" scoped>
    .card {
        position: relative;
        overflow: hidden;
        &__img {
            width: 100%;
            height: 26rem;
            img {
                object-fit: cover;
                width: 100%;
                height: 100%;
            }
        }
        &__info {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba($color: #2D3653, $alpha: .6);
            color: white;
            padding: 2.8rem 2rem;
            transform: translateY( 18.4rem);
            transition: all .6s ease;
            &--title {
                font-weight: 600;
                font-size: 2.4rem;
                line-height: 100%;
                margin-bottom: 2.8rem;
            }

            &--description {
                font-weight: 400;
                font-size: 1.7rem;
                line-height: 140%;
            }
        }
        &:hover &__info {
            transform: translateY(0rem);
        }
    }
</style>