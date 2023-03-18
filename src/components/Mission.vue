<template>
    <div class="mission">
        <h1 class="mission__text">
            <span>Softline</span> - ведущий поставщик IT-решений и сервисов.* Мы предлагаем комплексные IT-решения, 
                    облака, программное и аппаратное обеспечение, решения по цифровой трансформации и кибербезопасности, 
                    a также широкий спектр IT-услуг. 
        </h1>
        <div class="d-flex">
            <div class="mission__statistic col-4 col-sm-6">
                <p class="mission__statistic--number"> > 30 лет</p>
                <p class="mission__statistic--text">на IT-рынке</p>
            </div>
            <div class="mission__statistic col-4 col-sm-6">
                <p class="mission__statistic--number"> 4600</p>
                <p class="mission__statistic--text">сотрудников в России</p>
            </div>
            <div class="mission__statistic col-4 col-sm-6" >
                <p class="mission__statistic--number">25</p>
                <p class="mission__statistic--text">городов России</p>
            </div>
            <div class="mission__statistic col-6 col-sm-6">
                <p class="mission__statistic--number"> 2000 +</p>
                <p class="mission__statistic--text">разработчиков</p>
            </div>
            <div class="mission__statistic col-6 col-sm-12">
                <p class="mission__statistic--number">3000+</p>
                <p class="mission__statistic--text">сотрудников ежегодно проходят оценку и обучение</p>
            </div>
        </div>
    </div>

</template>
<script lang="ts">
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
import { defineComponent, onMounted } from 'vue';
    export default defineComponent({
        setup() {
            onMounted(() => {
                ScrollTrigger.create({
                    trigger: '.mission',
                    onEnter() {

                        gsap.from( (document.querySelector('.mission__text') as HTMLElement), {
                            y: -300,
                            x: 20,
                            duration: 2,
                        });


                        gsap.from( (document.querySelector('.d-flex') as HTMLElement), {
                            y: 300,
                            x: 20,
                            duration: 2,
                        })
                    }
                })
            })
        }
    })
</script>

<style lang="scss" scoped>
    $red: #B01736;
    $red-variant: #A30C33;
    $black: #444444;
    .mission {
        margin-top: 10rem;
        margin-right: 7rem;
        margin-left: 7rem;
        &__text {
            color: $black;
            font-size: 3.2rem;
            font-weight: 600;
            line-height: 120%;
            text-align: center;
            padding: 10rem 11rem;
            box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.08);
            span {
                color: $red;
            }
        }

        &__statistic {
            text-align: center;
            margin: 4rem 0;
            &--number {
                color: $red-variant;
                font-weight: 600;
                font-size: 8rem;
                line-height: 80%;
            }
            &--text {
                font-weight: 400;
                font-size: 1.8rem;
                line-height: 150%;
                color: $black;
            }
        }
    }

    @media screen and (max-width: 36rem) {
        .mission {
            margin-top: 6rem;
            margin-right: 0;
            margin-left: 0;

            &__text {
                font-size: 1.6rem;
                padding: 2.4rem .5rem;
            }

            &__statistic {
                margin: 2.4rem 0;
                &--number {
                    font-size: 4rem;
                }

                &--text {
                    font-size: 1.6rem;
                }
            }
        }
    }
</style>