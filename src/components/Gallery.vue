<template>
    <div class="gallery">
        <div class="header">
            <p class="header__title">
                Корпоративная жизнь
            </p>
            <div class="header__btns">
                <button class="header__btns--left" @click="onSelectImg(-1)">
                    <img :src="require('@/assets/svgs/left.svg')" alt="">
                </button>
                <button class="header__btns--right" @click="onSelectImg(1)">
                    <img :src="require('@/assets/svgs/right.svg')" alt="">
                </button>
            </div>
        </div>
        <div class="slider" ref="sliderRef">
            <div class="slider__item unselected " v-for="(img, i) in images" :class="{ 'selected': i == selectedImg }" :key="i">
                <img :src="img" alt="">
            </div>
        </div>
        <div class="slider-pagination">
            <div v-for="i in 5" :key="i" class="slider-pagination__item" :class="{'active':  i-1 == selectedImg }">
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import gsap from 'gsap';
import { Elastic, Power4 } from 'gsap';
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
import { onMounted, ref } from 'vue'
gsap.registerPlugin(ScrollTrigger);
export default {
    setup() {
        const selectedImg = ref(0);
        const sliderRef = ref<HTMLElement>();
        const images = ref([
            require('@/assets/images/slide1.jpg'),
            require('@/assets/images/slide2.jpg'),
            require('@/assets/images/slide3.jpg'),
            require('@/assets/images/slide4.jpg'),
            require('@/assets/images/slide5.jpg')
        ]);


        onMounted(() => {
            ScrollTrigger.create({
                trigger: '.gallery',
                onEnter(){
                    const tl = gsap.timeline()
                    tl.from('.header__title', {
                        x: 100,
                        opacity: .2,
                        ease: Elastic.easeIn,
                        duration: 1
                    });

                    tl.from('.header__btns', {
                        x: 200,
                        ease: Elastic.easeOut,
                        duration: 1
                    });

                    tl.from('.slider', {
                        y: 200,
                        opacity: 0,
                        ease: Power4.easeInOut
                    });
                    const paginations: HTMLElement = document.querySelector('.slider-pagination')!;
                    tl.from(paginations?.children, {
                        y: 50,
                        opacity: 0,
                        duration: .5,
                        ease: Elastic.easeInOut
                    })
                }
            })
        })


        const onSelectImg = (counter: number) => {
            console.log(counter);
            sliderRef.value?.children[selectedImg.value].classList.remove('selected');
            sliderRef.value?.children[selectedImg.value].classList.add('unselected');
            selectedImg.value = selectedImg.value + counter;
            const imageLen = images.value.length;
            if(selectedImg.value < 0) {
                selectedImg.value = imageLen - 1;
            }
            if(selectedImg.value > imageLen - 1) {
                selectedImg.value = 0;
            }
            sliderRef.value?.children[selectedImg.value].classList.add('selected');
            sliderRef.value?.children[selectedImg.value].classList.remove('unselected');
            const direction = Math.random();
            gsap.from('.selected', {
                y: direction> .5 ? Math.random() * 500: -Math.random() * 500,
                x: direction> .5 ? Math.random() * 500: -Math.random() * 500,
                duration: .6
            });
            
        }

        return {
            sliderRef,
            onSelectImg,
            images,
            selectedImg
        }
    }
}
</script>
<style lang="scss" scoped>
    .header {
        display: flex;
        margin-bottom: 5rem;
        justify-content: space-between;
        &__title {
            font-weight: 600;
            font-size: 5.6rem;
            line-height: 100%;
        }

        &__btns {
            display: flex;
            gap: 2rem;
            button {
                border: none;
                outline: none;
                padding: 1.8rem 2.4rem;
                border-radius: 50%;
                aspect-ratio: 1/1;
            }
        }
    }

    .slider {
        position: relative;
        width: 100%;
        height: 83.5rem;
        margin-bottom: 4rem;
        overflow: hidden;
        &__item {
            position: absolute;
            width: 100%;
            height: 100%;
            transition: 1s all ease !important;
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }

            &.unselected {
                opacity: 0;
                display: none;
            }
            &.selected {
                display: unset;
                opacity: 1;
            }
        }

        &-pagination {
            display: flex;
            gap: 1rem;
            margin-bottom: 5.6rem;
            &__item {
                height: .4rem;
                background: #000000;
                opacity: 0.1;
                width: 100%;

            }
            .active {
                background: #A30C33 !important;
                opacity: 1;
            }
        }
    }
</style>