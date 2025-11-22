<!-- src/organisms/OrganismHome.vue -->
<script setup lang="ts">
import MoleculeBigCarousel from "../molecules/MoleculeBigCarousel.vue";
import { MoleculeMobileCarousel, MoleculeChannel, MoleculeBodyCarousel } from "../molecules";

import {
    CruellaBanner,
    FirstBanner,
    LastBanner,
    MobileSereia,
    MobileCartton,
    NemoBanner,
    Star,
    StarWars,
    Pixar,
    Geographic,
    Marvel,
    Disney,
    Simpsons,
    Side,
    Moon
} from "../../assets/img";

// Dados do componente
const banners = [
    CruellaBanner,
    FirstBanner,
    LastBanner
];
const items = [
    MobileCartton,
    MobileSereia,
    NemoBanner,
    MobileSereia
];
const channels = [
    Star,
    Geographic,
    Pixar,
    Marvel,
    StarWars,
    Disney
];
const recomendation =[
    Simpsons,
    Side,
    Moon
]
const swiperConfig = {
    slidesPerView: 1.2,
    centeredSlides: true,
    spaceBetween: 20,
    loop: true,
    autoplay: { delay: 3000, disableOnInteraction: false }
};

const desktopConfig = {
    slidesPerView: 1,
    loop: true,
    autoplay: { delay: 3000, disableOnInteraction: false }
};
</script>

<template>
    <div class="bg-(--body) flex flex-col gap-y-3 sm:gap-y-10">
        <div class="carousel">
            <MoleculeBigCarousel class="hidden sm:block" :items="banners" :swiperOptions="desktopConfig">
                <template #slide="{ item }">
                    <img :src="item" class="w-full h-64 object-cover rounded-xl" alt="banner" />
                </template>
            </MoleculeBigCarousel>

            <MoleculeMobileCarousel class="sm:hidden" :items="items" :swiperOptions="swiperConfig">
                <template #slide="{ item }">
                    <img :src="item" class="object-contain w-full h-full" />
                </template>
            </MoleculeMobileCarousel>
        </div>

        <div class="channels">
            <MoleculeChannel class="flex flex-wrap justify-center gap-2" :items="channels" />
        </div>

        <div class="recomendations">
            <MoleculeBodyCarousel :items="recomendation" :swiperOptions="swiperConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>
                       
                </template>
            </MoleculeBodyCarousel>

        </div>
    </div>
</template>

<style></style>
