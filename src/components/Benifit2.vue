
import BenifitCard from './Card/BenifitCard.vue';


import BenifitCard from './Card/BenifitCard.vue';

<template>
    <section class="benifit">
        <h1 class="benifit--pakets-title">Компенсационный пакет</h1>
        <div class="benifit__pakets">
            <BenifitCard :img="require('@/assets/svgs/Frame 18625238.svg')" :title="'Дмс'"/>
            <BenifitCard :img="require('@/assets/svgs/Frame 18625240.svg')" :title="'Выходной в день рождения'"/>
            <BenifitCard :img="require('@/assets/svgs/Frame 18625242.svg')" :title="'Корпоративная мобильная связь'"/>
            <BenifitCard :img="require('@/assets/svgs/Frame 18625244.svg')" :title="'Корпоративные скидки на спорт'"/>
            <BenifitCard class="last-card" :img="require('@/assets/svgs/Vector.svg')" :title="'LTI'"/>
        </div>
        <h1 class="benifit--programm-title">Программа дополнительной мотивации</h1>
        <h1 class="benifit--programm-subtitle">доплата 12% от суммы</h1>
        <div class="benifit__programm">
            <BenifitCard :img="require('@/assets/svgs/Frame 18625247.svg')" :title="'Дмс'"/>
            <BenifitCard :img="require('@/assets/svgs/Frame 18625238.svg')" :title="'Выходной в день рождения'"/>
            <BenifitCard class="last-card" :img="require('@/assets/svgs/Icon.svg')" :title="'Корпоративная мобильная связь'"/>
        </div>
        
    </section>
</template>
<script lang="ts">
import gsap, { Bounce} from 'gsap';
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger';
import BenifitCard from './Card/BenifitCard.vue';
import { onMounted } from 'vue';

export default {
    components: { 
        BenifitCard
    },
    setup() {
        onMounted(() => {
            ScrollTrigger.create({
                trigger: '.benifit',
                onEnter() {
                    const tl = gsap.timeline();
                    tl.from(['.benifit--pakets-title', 
                        '.benifit--programm-title', 
                        '.benifit--programm-subtitle'
                    ], {
                        y: 150,
                        duration: .5,
                        ease: Bounce.easeInOut
                    });

                    tl.from([document.querySelector('.benifit__pakets')?.children,
                        document.querySelector('.benifit__programm')?.children], {
                            x: -150,
                            duration: 1,
                            ease: Bounce.easeIn
                        })
                }
            })
        })
    }
}
</script>
<style lang="scss" scoped>
    $black: #444444;
    $red: #B01736;
    .benifit {
        margin-top: 18rem;

        &--pakets-title {
            font-weight: 600;
            font-size: 5.6rem;
            line-height: 100%;
            text-align: center;
            color: #444444;
            margin-bottom: 5rem;
        }

        &__pakets {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            grid-gap: 2rem;
        }

        &--programm-title {
            margin-top: 14rem;
            margin-bottom: .4rem;
            text-align: center;
            font-weight: 600;
            font-size: 4rem;
            line-height: 120%;
        }

        &--programm-subtitle {
            text-align: center;
            font-weight: 600;
            font-size: 4rem;
            line-height: 120%;
            color: $red;
        }

        &__programm {
            margin: 5rem 31rem;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
        }
    }

    @media screen and (max-width: 36rem) {
        .benifit {
            margin-top: 7.4rem;

            &--pakets-title {
                font-size: 2.8rem;
            }

            &__pakets {
                grid-template-columns: repeat(2, 1fr);
                .last-card {
                    grid-column: 1/3;
                }
            }
            &--programm-title {
                font-size: 2.2rem;
            }

            &--programm-subtitle {
                font-size: 2.2rem;
            }
            
            &__programm {
                grid-template-columns: repeat(2, 1fr);
                margin: 2.5rem auto;
                gap: 1rem;

                .last-card {
                    grid-column: 1/3;
                }
            }
        }
    }
</style>