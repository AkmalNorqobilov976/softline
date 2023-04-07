<template>
    <section class="mission2" ref="mission2Ref">
        <h1 class="mission2__title">
            Миссия Softline
        </h1>
        <p class="mission2__info">
            Мы помогаем организациям трансформироваться, работать эффективно и безопасно  в условиях цифровой экономики.
        </p>
    </section>
</template>
<script lang="ts">
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
export default {
    setup() {
        const mission2Ref = ref<HTMLElement>()!;
        onMounted(() => {
            ScrollTrigger.create({
                trigger: mission2Ref.value,
                onEnter() {
                    gsap.from((mission2Ref.value as HTMLElement)?.children[0], {
                        duration: .5,
                        opacity: 0,
                        y: 100,
                        ease: 'Bounce.easeIn'
                    });
                    gsap.from((mission2Ref.value as HTMLElement)?.children[1], {
                        delay: .5,
                        opacity: 0,
                        x: 100,
                        duration: 1,
                        ease: 'Bounce.easeIn'
                    })
                }
            })
        });

        return {
            mission2Ref
        }
    }
}
</script>
<style lang="scss" scoped>
    $red: #A30C33;
    .mission2 {
        margin: 10rem 0;
        padding: 14rem 7rem;
        background-color: rgba($color: $red, $alpha: .7);
        background: url('@/assets/images/Left\ pattern.png') no-repeat left center, url('@/assets/images/Right\ pattern.png') no-repeat right center, rgba($color: $red, $alpha: .7);
        color: white;
        text-align: center;
        
        &__title {
            font-weight: 600;
            font-size: 5.6rem;
            line-height: 100%;
            margin-bottom: 4rem;
        }

        &__info {
            font-weight: 400;
            font-size: 3.2rem;
            line-height: 150%;
        }

    }

    @media screen and (max-width: 60rem) {
        .mission2 {
            margin: 5rem 0;
            padding: 5rem .5rem;
            background-size: 17rem 17rem;

            &__title {
                font-size: 2.8rem;
                margin-bottom: 1rem;
            }

            &__info {
                font-size: 1.6rem;
            }
        }
    }
</style>