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
    NemoBanner,
    MobileSereia
];

const swiperConfig = {
    slidesPerView: 1.2,
    centeredSlides: true,
    spaceBetween: 20,
    loop: true,
    autoplay: {
        delay: 3000,
        disableOnInteraction: false,
    }
};



const desktopConfig = {
    slidesPerView: 1,
    loop: true,
    autoplay: {
        delay: 3000,
        disableOnInteraction: false,
    }
};



</script>

<template>
    <div class="header">
        <Header />
    </div>
    <MoleculeBigCarousel class="hidden sm:block" :items="banners" :swiperOptions="desktopConfig">
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