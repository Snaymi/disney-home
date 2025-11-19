<template>
    <div class="header">
        <Header />
    </div>
    <MoleculeBigCarousel :items="banners" :swiperOptions="{
        slidesPerView: 1,
        loop: true
    }">
        <template #slide="{ item }">
            <img :src="item" class="w-full h-64 object-cover rounded-xl" alt="banner" />
        </template>
    </MoleculeBigCarousel>




</template>

<script setup>
import Header from '../organisms/Header.vue';
import MoleculeBigCarousel from '../molecules/MoleculeBigCarousel.vue';
import cruellaBanner from "../../assets/img/cruella-banner.webp";
import firstBanner from "../../assets/img/first-banner.webp"
import lastBanner from "../../assets/img/second-banner.webp"
const banners = [
    cruellaBanner,
    firstBanner,
    lastBanner,
];



</script>

<style lang="scss" scoped>
.header {
    background-color: var(--header);
}
</style>