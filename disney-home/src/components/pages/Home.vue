<script setup>
import Header from '../organisms/Header.vue';
import MoleculeBigCarousel from '../molecules/MoleculeBigCarousel.vue';
import { MoleculeMobileCarousel } from "../molecules"
import {
    CruellaBanner,
    FirstBanner,
    LastBanner,
    MobileSereia,
    MobileCartton,
    NemoBanner
} from '../../assets/img';

const banners = [
    CruellaBanner,
    FirstBanner,
    LastBanner,
];
const items = [
    MobileCartton,
    MobileSereia,
    NemoBanner
];

const swiperConfig = {
  slidesPerView: 1.2,     // mostra 1 inteiro e um pedaço do próximo
  centeredSlides: true,   // centraliza o slide visível
  spaceBetween: 20,
  freeMode: false,
  pagination: {
    el: ".swiper-pagination",
    clickable: true,
  },
};





</script>

<template>
    <div class="header">
        <Header />
    </div>
    <MoleculeBigCarousel class="hidden sm:block" :items="banners" :swiperOptions="{
        slidesPerView: 1,
        loop: true
    }">
        <template #slide="{ item }">
            <img :src="item" class="w-full h-64 object-cover rounded-xl" alt="banner" />
        </template>
    </MoleculeBigCarousel>


    <MoleculeMobileCarousel class="sm:hidden" :items="items" :swiperOptions="swiperConfig">
        <template #slide="{ item }">
            <img :src="item" class="object-cover w-full h-full" />
        </template>
    </MoleculeMobileCarousel>

</template>



<style lang="scss" scoped>
.header {
    background-color: var(--header);
}
</style>