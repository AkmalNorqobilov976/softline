<template>
    <div class="card" ref="cardRef" :class="{ toggle }">
        <div class="card__img">
            <img :src="img" alt="" />
        </div>
        <div class="card__info">
            <p @click="toggle = !toggle" class="card__info--title">{{ title }} <span  :class="{rotate: toggle}"><img :src="require('@/assets/svgs/arrow-down.svg')" alt=""/></span></p>
            <p class="card__info--description">{{ description }}</p>
        </div>
    </div>
</template>

<script lang="ts">
import gsap from 'gsap'
import { defineComponent, onMounted, ref, watch } from "vue";
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)
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
   },

   setup() {
        const toggle = ref(false);
        const cardRef = ref<HTMLElement>()!;
        const tl = gsap.timeline();
        watch(toggle, (newValue) => {
            console.log(newValue);
            
            tl.to((cardRef.value as HTMLElement), {
                height: toggle.value ? '26rem' : '7.6rem',
                duration: .5
            })
        });

        // onMounted(() => {
        //     const direction = Math.random();
        //     ScrollTrigger.create({
        //         trigger: '.benifit',
        //         onEnter() {
        //             gsap.from(cardRef.value as HTMLElement, {
        //                 opacity: 1,
        //                 // delay: .3,
        //                 // y: direction> .5 ? Math.random() * 500: -Math.random() * 500,
        //                 // x: direction> .5 ? Math.random() * 500: -Math.random() * 500,
        //             })
        //         }
        //     })
        // })

        return {
            toggle,
            cardRef
        }
   }
});
</script>

<style lang="scss" scoped>
    .card {
        position: relative;
        overflow: hidden;
        transition: all .5s ease !important;
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
                display: flex;
                justify-content: space-between;
                align-items: baseline;
                span {
                    display: none;
                    img {
                        width: 1.5rem;
                        height: 1.5rem;
                    }
                }
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

    @media screen and (max-width: 60rem) {
        .card {
            height: 7.6rem;
            
            &__info {
                transform: translateY(0rem);
                padding: 2.5rem 2rem;

                &--title {
                    span {
                        display: unset;
                    }
                }
            }

        }
        .toggle {
            height: 26rem;
        }
    }
</style>