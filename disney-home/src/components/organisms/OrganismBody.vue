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
    Moon,
    Nate,
    Anotomy,
    Baymax,
    Ice,
    Red,
    Allfy,
    Olivia,
    Chip,
    Msmarvel,
    Duck,
    Kenobi,
    Sneak,
    Cruella,
    Encanto,
    Icev,
    Zack,
    Run,
    John,
    Iron,
    This,
    Faye
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
const recomendation = [
    Simpsons,
    Side,
    Moon,
    Nate,
    Anotomy,
    Baymax
]
const newPrograms = [
    Nate,
    Anotomy,
    Baymax,
    Ice,
    Red,
    Allfy,
    Olivia
]
const swiperConfig = {
    slidesPerView: 1.2,
    centeredSlides: true,
    spaceBetween: 20,
    loop: true,
    autoplay: { delay: 3000, disableOnInteraction: false }
};
const swiperBodyConfig = {
    slidesPerView: "auto",
    centeredSlides: true,
    spaceBetween: 20,
    loop: true,
    autoplay: { delay: 3000, disableOnInteraction: false }
}

const desktopConfig = {
    slidesPerView: 1,
    loop: true,
    autoplay: { delay: 3000, disableOnInteraction: false }
};
const proximos = [
    Chip,
    Msmarvel,
    Duck,
    Kenobi,
    Sneak
]
const comedy = [
    Nate,
    Cruella,
    Encanto,
    Icev,
    Zack,
    Chip
]
const action = [
    Zack,
    Run,
    John,
    Iron,
    This,
    Faye
]

</script>

<template>
    <div class="bg-(--body) flex flex-col gap-y-2 sm:gap-y-3 max-w-[1350px]">
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

        <div class="channels lg:mt-[65px]">
            <MoleculeChannel class="flex flex-wrap justify-center gap-2" :items="channels" />
        </div>

        <div class="recomendations pl-4 pr-4 mt-5">
            <h2 class="text-start sm:mb-[30px]">
                Recomendações para você
            </h2>
            <MoleculeBodyCarousel :items="recomendation" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>

        </div>
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Novos na Disney+
            </h2>
            <MoleculeBodyCarousel :items="newPrograms" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>

        </div>
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Próximos
            </h2>
            <MoleculeBodyCarousel :items="proximos" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[405px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>
        </div>
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Comédia
            </h2>
            <MoleculeBodyCarousel :items="comedy" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>

        </div>
        
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Ação
            </h2>
            <MoleculeBodyCarousel :items="action" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>

        </div>
    </div>
</template>

<style>
* {
    box-sizing: border-box;
    margin: 0;
}
</style>
