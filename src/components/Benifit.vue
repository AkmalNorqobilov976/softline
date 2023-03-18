
import Card from './Card/Card.vue';

<template>
    <div class="benifit">
        <h1 class="benifit__title">
            Направления бизнеса
        </h1>
        <div class="benifit__card">
            <Card 
                :img="require('@/assets/images/img1.jpg')"
                title="Решения Softline" 
                description="ГК Softline предлагает клиентам собственную линейку оборудования (ПК, серверы, торговое оборудование и 
                проч.), разработку программных продуктов, облачных решений, решений 
                в области информационной безопасности."/>

            <Card 
                :img="require('@/assets/images/img2.jpg')"
                title="Кибербезопасность" 
                description="Softline обладает всеми необходимыми государственными лицензиями для организации проектов по информационной безопасности и аттестации."/>
            
            <Card 
                :img="require('@/assets/images/img3.jpg')"
                title="Импортозамещение" 
                description="ГК Softline обладает широчайшим портфелем решений и услуг для импортозамещения, включая ПО и оборудование собственного производства."
            />
            <Card 
                :img="require('@/assets/images/img4.jpg')"
                title="Облачные решения" 
                description="Softline использует современные облачные решения как российских, так и международных вендоров для масштабирования бизнеса своих клиентов. Подписки, услуги, трансформация."/>
            
            <Card 
                :img="require('@/assets/images/img5.jpg')"
                title="Цифровая трансформация и разработка ПО" 
                description="Softline использует современные технологи и новые возможности для увеличения производительности бизнеса заказчика. В штате ГК Softline - 2000+ разработчиков, которые трансформируют ПО под нужды конкретного предприятия."
            />
            
            <Card 
            :img="require('@/assets/images/img6.jpg')"
            title="Техническая поддержка Softline" 
            description="200+ инженеров, 24 часа в сутки, 7 дней в неделю, 12 месяцев в году, сервисное партнерство с 30+ мировыми производителями."/>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from "vue";
import Card from "./Card/Card.vue";
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
export default defineComponent({
    components: {
        Card,
    },
    setup() {
        onMounted(() => {
            ScrollTrigger.create({
                trigger: '.benifit',
                onEnter() {
                    const tl = gsap.timeline();
                    tl.from('.benifit__title', {
                        y: 100,
                        x: 100,
                        opacity: 0,
                        duration: 1
                    });
                    
                }
            })
        })
    }
})
</script>

<style lang="scss" scoped>
    .benifit {
        &__title {
            font-weight: 600;
            font-size: 5.6rem;
            line-height: 100%;
            padding: 5.5rem;
            text-align: center;
        }

        &__card {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }
    }

    @media screen and (max-width: 36rem) {
        .benifit {
            &__title {
                font-size: 2.8rem;
                padding: 0;
                margin-bottom: 1.5rem;
            }
            &__card {
                grid-template-columns: 1fr;
            }
        }
    }
</style>