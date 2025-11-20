<script setup>
import Header from '../organisms/Header.vue';
import MoleculeBigCarousel from '../molecules/MoleculeBigCarousel.vue';
import {MoleculeMobileCarousel} from "../molecules"
import { CruellaBanner,
         FirstBanner,
         LastBanner
 } from '../../assets/img';

const banners = [
    CruellaBanner,
    FirstBanner,
    LastBanner,
];
const items = [

]


</script>

<template>
    <div class="header">
        <Header />
    </div>
    <MoleculeBigCarousel class="hidden lg:block" :items="banners" :swiperOptions="{
        slidesPerView: 1,
        loop: true
    }">
        <template #slide="{ item }">
            <img :src="item" class="w-full h-64 object-cover rounded-xl" alt="banner" />
        </template>
    </MoleculeBigCarousel>


    <!-- <MoleculeMobileCarousel :items="icons" :swiperOptions="swiperConfig">
        <template #slide="{ item }">
            <img :src="item" class="w-20 h-20 object-cover rounded-full" />
        </template>
    </MoleculeMobileCarousel> -->

</template>



<style lang="scss" scoped>
.header {
    background-color: var(--header);
}
</style>