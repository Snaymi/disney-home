<!-- src/organisms/OrganismHome.vue -->
<script setup lang="ts">
import MoleculeBigCarousel from "../molecules/MoleculeBigCarousel.vue";
import { MoleculeMobileCarousel, MoleculeChannel, MoleculeBodyCarousel, MoleculeModal } from "../molecules";
import { ref } from "vue";
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
    Faye,
    modalCruella,
    modalSimpsons,
    modalMsMarvel
} from "../../assets/img";

// defina isso logo depois dos imports
export interface MediaItem {
  id: number;
  title: string;
  image: string;
  modalImage: string;
  year?: number;
  duration?: string;
  rating?: string;
  genre?: string[];
  description?: string;
  tags?: string[];

  // você pode adicionar campos específicos, mas sempre opcionais
}



// Dados do componente
const banners: MediaItem[] = [
    {
        id: 101,
        title: "Cruella",
        image: CruellaBanner,
        modalImage: modalCruella,
        year: 2021,
        duration: "2h 14min",
        rating: "12",
        genre: ["Comédia", "Crime", "Drama"],
        description:
            "A história da jovem Estella antes de se tornar a lendária vilã Cruella de Vil. Moda, rebeldia e vingança se misturam nesta origem estilosa.",
        tags: ["Filme", "Original Disney+", "Live-Action"],
    },

    {
        id: 102,
        title: "Raya e o Último Dragão",
        image: FirstBanner,
        modalImage: modalSimpsons,
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 103,
        title: "Luca",
        image: LastBanner,
        modalImage: modalMsMarvel,
        year: 2021,
        duration: "1h 35min",
        rating: "Livre",
        genre: ["Comédia", "Fantasia", "Família"],
        description:
            "Luca vive um inesquecível verão italiano cheio de amizade, sorvete e segredos — como o fato de ser uma criatura marinha fora d’água.",
        tags: ["Pixar", "Amizade", "Família"],
    },
];
const items: string[] = [
    MobileCartton,
    MobileSereia,
    NemoBanner,
    MobileSereia
];
const channels: string[] = [
    Star,
    Geographic,
    Pixar,
    Marvel,
    StarWars,
    Disney
];
const recomendation: string[] = [
    Simpsons,
    Side,
    Moon,
    Nate,
    Anotomy,
    Baymax
]
const newPrograms: string[] = [
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

const proximos: string[] = [
    Chip,
    Msmarvel,
    Duck,
    Kenobi,
    Sneak
]

const comedy: string[] = [
    Nate,
    Cruella,
    Encanto,
    Icev,
    Zack,
    Chip
]

const action: string[] = [
    Zack,
    Run,
    John,
    Iron,
    This,
    Faye
]

const modalOpen = ref(false);
const modalItem = ref<MediaItem | null>(null);
function openModal({ item, index }) {
    modalItem.value = item; // aqui você coloca objeto depois
    modalOpen.value = true;
}

</script>

<template>
    <div class="bg-(--body) flex flex-col gap-y-2 sm:gap-y-3 max-w-[1350px]">
        <div class="carousel">
            <MoleculeBigCarousel class="hidden sm:block" :items="banners" :swiperOptions="desktopConfig"
                @slide-click="openModal">
                <template #slide="{ item }">
                    <img :src="item.image" class="w-full h-64 object-cover rounded-xl" alt="banner" />
                </template>
            </MoleculeBigCarousel>

            <MoleculeMobileCarousel class="sm:hidden" :items="items" :swiperOptions="swiperConfig">
                <template #slide="{ item }">
                    <img :src="item" class="object-contain w-full h-full" />
                </template>
            </MoleculeMobileCarousel>
            <MoleculeModal v-model="modalOpen">
                <!-- Conteúdo que você quer testar -->
                <div class="p-4 flex flex-col items-center gap-4">
                    <h2 class="text-xl font-bold">Item clicado:</h2>
                    <img :src="modalItem?.modalImage" class="w-[90vw] h-[80vh] rounded-xl" />
                </div>
            </MoleculeModal>

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
