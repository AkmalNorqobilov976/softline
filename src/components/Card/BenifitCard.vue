<template>
    <div class="benifit-card">
        <div class="benifit-card__img">
            <img :src="img" alt="">
        </div>
        <p class="benifit-card__title">{{ title }}</p>
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
            }
        }
    })
</script>

<style lang="scss" scoped>
    .benifit-card {
        text-align: center;

        &__img {
            margin: auto;
            width: 8rem;
            height: 8rem;
            border-radius: 50%;
            background: rgba($color: #000000, $alpha: .05);
            padding: 3rem;
            display: flex;
            justify-content: center;
            align-items: center;            
            img {
                width: 4.8rem;
                height: 4.8rem;
            }
        }

        &__title {
            margin-top: 1rem;
            padding: 0 2rem;
            text-align: center;
            font-weight: 400;
            font-size: 1.8rem;
            line-height: 110%;
        }
    }
</style>