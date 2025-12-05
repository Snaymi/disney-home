<!-- src/organisms/OrganismHome.vue -->
<script setup lang="ts">
import MoleculeBigCarousel from "../molecules/MoleculeBigCarousel.vue";
import { LoadingSpinner, AtomButtonPlay } from "../atoms";
import { MoleculeMobileCarousel, MoleculeChannel, MoleculeBodyCarousel, MoleculeModal } from "../molecules";
import { ref } from "vue";
import {
    modalSide,
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
    modalMsMarvel,
    playIcon
} from "../../assets/img";

// defina isso logo depois dos imports
export interface MediaItem {
    id: number;
    title: string;
    image: string;
    modalImage: string;
    youtubeUrl?: string;
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
        youtubeUrl: "https://www.youtube.com/embed/tflvpp467hc?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
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
        title: "Simpsons",
        image: FirstBanner,
        modalImage: modalSimpsons,
        youtubeUrl: "https://www.youtube.com/embed/7UPVGlMjPLw?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
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
        title: "MsMarvel",
        image: LastBanner,
        modalImage: modalMsMarvel,
        youtubeUrl: "https://www.youtube.com/embed/tz9ghPTmyN4?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
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
const recomendation: MediaItem[] = [
    {
        id: 104,
        title: "Simpsons",
        image: FirstBanner,
        modalImage: modalSimpsons,
        youtubeUrl: "https://www.youtube.com/embed/7UPVGlMjPLw?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 105,
        title: "West Side Story",
        image: Side,
        modalImage: modalSide,
        youtubeUrl: "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 106,
        title: "Moon",
        image: Moon,
        modalImage: modalSide,
        youtubeUrl: "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 107,
        title: "Nate",
        image: Nate,
        modalImage: modalSide,
        youtubeUrl: "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 108,
        title: "Anotomy",
        image: Anotomy,
        modalImage: modalSide,
        youtubeUrl: "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 110,
        title: "Baymax",
        image: Baymax,
        modalImage: modalSide,
        youtubeUrl: "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Raya embarca em uma missão épica para encontrar o lendário último dragão e restaurar a paz em seu reino dividido.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    }
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
const loading = ref(false);
const showVideo = ref(false);

async function openModal({ item }) {
    loading.value = true;
    showVideo.value = false;
    modalItem.value = null;
    modalOpen.value = true;

    await new Promise(resolve => setTimeout(resolve, 2000));

    modalItem.value = item;
    loading.value = false;
}

function playVideo() {
    showVideo.value = true;
}

function close() {
    modalOpen.value = false;
    showVideo.value = false;
    modalItem.value = null; // limpa para não deixar vídeo rodando
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



        </div>

        <div class="channels lg:mt-[65px]">
            <MoleculeChannel class="flex flex-wrap justify-center gap-2" :items="channels" />
        </div>

        <div class="recomendations pl-4 pr-4 mt-5">
            <h2 class="text-start sm:mb-[30px]">
                Recomendações para você
            </h2>
            <MoleculeBodyCarousel @slide-click="openModal" :items="recomendation" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item.image" class="w-full h-full object-cover rounded-xl" />
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
    <MoleculeModal v-model="modalOpen">
        <div class="relative min-h-[200px] min-w-[200px] flex items-center justify-center">

            <!-- SPINNER -->
            <LoadingSpinner v-if="loading" />
            <div v-else-if="showVideo" class="w-full h-full flex justify-center items-center">
                <iframe :src="modalItem?.youtubeUrl" frameborder="0" class="w-[90vw] h-[90vh] rounded"
                    allowfullscreen></iframe>
            </div>


            <!-- CONTEÚDO REAL -->
            <div v-else class="p-4 flex flex-col items-center gap-4">
                <img :src="modalItem?.modalImage"
                    class="rounded-xl object-contain relative hover:brightness-[0.1] transition-all duration-500" />
                <AtomButtonPlay class="absolute cursor-pointer top-[50%] bg-white" label="PLAY" :icon="playIcon"
                    size="md" variant="default" @click="playVideo" />
                <button class="absolute right-3 top-3 text-zinc-700 hover:text-black" @click="close"
                    aria-label="Fechar">
                    ✕
                </button>
                <p class="text-center font-bold w-[800px] text-xl absolute top-[60%]">
                    {{ modalItem?.description }}
                </p>
            </div>
        </div>
    </MoleculeModal>
</template>

<style>
* {
    box-sizing: border-box;
    margin: 0;
}
</style>
