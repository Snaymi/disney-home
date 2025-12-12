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
    playIcon,
    modalBaymax,
    modalNate,
    modalMoon,
    modalGray,
    modalAlley,
    modalEye,
    modalChip,
    modalJustice,
    modalScrat,
    modalEncanto,
    modalRed,
    modalUs,
    modalIron,
    modalKerella,
    modalWan,
    modalIce,
    modalDuck,
    modalOlivia,
    verticalMsMarvel
} from "../../assets/img";
import { get } from "http";


// --------------------------------------------
//  MEDIA ITEM TYPE
// --------------------------------------------
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
}


// --------------------------------------------
//  MEDIA STORE UNIVERSAL
// --------------------------------------------
const mediaStore: MediaItem[] = [];

function register(...items: MediaItem[]) {
    mediaStore.push(...items);
}

const getMedia = (id: number) =>
    mediaStore.find(item => item.id === id) || null;


// --------------------------------------------
//  BANNERS
// --------------------------------------------
//  BANNERS
// --------------------------------------------
const banners: MediaItem[] = [
    {
        id: 101,
        title: "Cruella",
        image: CruellaBanner,
        modalImage: modalCruella,
        youtubeUrl:
            "https://www.youtube.com/embed/tflvpp467hc?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
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
        youtubeUrl:
            "https://www.youtube.com/embed/7UPVGlMjPLw?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Os Simpsons é uma sátira animada da vida americana, centrada na disfuncional família Simpson (Homer, Marge, Bart, Lisa e Maggie) na fictícia cidade de Springfield, abordando humor, cultura e a condição humana através das desventuras de seus personagens, especialmente o preguiçoso Homer na usina nuclear e a inteligente Lisa, enquanto satirizam a sociedade, a televisão e a família tradicional, com a série sendo um fenômeno global.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 103,
        title: "MsMarvel",
        image: LastBanner,
        modalImage: modalMsMarvel,
        youtubeUrl:
            "https://www.youtube.com/embed/tz9ghPTmyN4?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 35min",
        rating: "Livre",
        genre: ["Comédia", "Fantasia", "Família"],
        description:
            "Kamala Khan, uma adolescente muçulmana gamer e fã de super-heróis (especialmente a Capitã Marvel) de Jersey City, que se sente deslocada, mas vê sua vida mudar ao ganhar superpoderes cósmicos, tendo que equilibrar sua vida normal com sua nova identidade de heroína, tudo isso enquanto explora sua cultura e laços familiares.",
        tags: ["Pixar", "Amizade", "Família"],
    },
];

// registra banners
register(...banners);


// --------------------------------------------
//  RECOMMENDATION
// --------------------------------------------
const recomendation: MediaItem[] = [
    getMedia(102)!, //simpsons

    {
        id: 105,
        title: "West Side Story",
        image: Side,
        modalImage: modalSide,
        youtubeUrl:
            "https://www.youtube.com/embed/fytEBjr7X58?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
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
        modalImage: modalMoon,
        youtubeUrl:
            "https://www.youtube.com/embed/DFa0evfX96s?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Steven Grant, um funcionário gentil com insônia, que descobre ter Transtorno Dissociativo de Identidade (TDI) e compartilha o corpo com o mercenário Marc Spector, o avatar do deus egípcio da lua, Khonshu, tornando-se o Cavaleiro da Lua. A trama segue suas jornadas confusas e perigosas enquanto lidam com inimigos e mistérios envolvendo a mitologia egípcia, questionando a realidade entre suas identidades e os eventos sobrenaturais que envolvem, como o culto de Arthur Harrow.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 107,
        title: "Nate",
        image: Nate,
        modalImage: modalNate,
        youtubeUrl:
            "https://www.youtube.com/embed/TPP54qgzZS0?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Nate Foster, um garoto de 13 anos apaixonado por musicais, mas completamente ignorado pela própria escola quando o assunto é talento. Nate sonha com Broadway do mesmo jeito que outros sonham com videogame novo: com brilho no olho e zero noção das probabilidades. Quando seus pais viajam e ninguém está olhando, ele e sua melhor amiga Libby bolam um plano maluco para fugir para Nova York e tentar uma audição de verdade.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 108,
        title: "Anotomy",
        image: Anotomy,
        modalImage: modalGray,
        youtubeUrl:
            "https://www.youtube.com/embed/A7TgB4t_6Jw?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Meredith Grey, residente (depois cirurgiã lendária) que entra no Seattle Grace Hospital e descobre que medicina é só metade da batalha; a outra metade é sobreviver ao tsunami emocional provocado por amores proibidos, dilemas éticos, perdas devastadoras e plantões que parecem universos paralelos. Entre cirurgias improváveis e amizades que viram família, a série usa o hospital como palco para examinar vulnerabilidade humana, ambição, culpa e aquilo que mantém as pessoas de pé mesmo quando o chão vive desabando.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 110,
        title: "Baymax",
        image: Baymax,
        modalImage: modalBaymax,
        youtubeUrl:
            "https://www.youtube.com/embed/fKTzCunAsI8?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Hiro Hamada é um jovem inventor brilhante que perde o irmão em um acidente misterioso. A única pista que sobra é um robô inflável de cuidados médicos: Baymax, uma espécie de enfermeiro gentil em forma de marshmallow tecnológico. Ao descobrir que o acidente não foi tão acidental assim, Hiro transforma sua dor em missão e, com Baymax e um grupo improvável de amigos, monta um time de heróis científicos. A jornada mistura humor, afeto e aquele tipo de aventura que deixa o coração quentinho enquanto brinca com temas de luto, amizade e responsabilidade.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
];

// registra recommendation
register(...recomendation);


// --------------------------------------------
//  NEW PROGRAMS
// --------------------------------------------
const newPrograms: MediaItem[] = [
    getMedia(107)!, // Nate
    getMedia(110)!, // Baymax
    getMedia(108)!, // Anatomy

    {
        id: 111,
        title: "Era Do Gelo",
        image: Ice,
        modalImage: modalIce,
        youtubeUrl:
            "https://www.youtube.com/embed/rVQelqH7dH4?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "A Era do Gelo: As Aventuras de Buck Wild (The Ice Age Adventures of Buck Wild) é um filme derivado da franquia que foca nos gambás Crash e Eddie, que, buscando independência de Ellie, se aventuram no perigoso Mundo Perdido, um ecossistema subterrâneo de dinossauros, onde são resgatados por Buck Wild, a doninha caolha e aventureira; juntos, eles precisam enfrentar uma nova ameaça de dinossauros rebeldes para salvar o local, com foco em temas de amizade, família e individualidade.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 112,
        title: "Red",
        image: Red,
        modalImage: modalRed,
        youtubeUrl:
            "https://www.youtube.com/embed/V2Xlg8WOS-Q?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Crescer é uma Fera conta a história de Mei, uma garota de 13 anos que se transforma em um panda-vermelho gigante toda vez que sente uma emoção forte.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 113,
        title: "Nightmare Alley",
        image: Allfy,
        modalImage: modalAlley,
        youtubeUrl:
            "https://www.youtube.com/embed/C7OIbiD8wYg?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "O ambicioso vigarista Stanton Carlisle, que tem um talento para manipular pessoas, se une a uma clarividente e seu marido mentalista para enganar um perigoso magnata com a ajuda de uma misteriosa psiquiatra, que pode ser sua maior oponente.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 114,
        title: "Olivia Rodrigo: driving home 2 u",
        image: Olivia,
        modalImage: modalOlivia,
        youtubeUrl:
            "https://www.youtube.com/embed/Ksji3ZXcu9E?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Olivia Rodrigo: Dirigindo até Você (Disney+) foca na criação do álbum SOUR, com a cantora viajando de Salt Lake City, compartilhando memórias e emoções sobre seu sucesso e vida.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
];


// registra newPrograms
register(...newPrograms);


// --------------------------------------------
//  IMAGENS DE OUTRAS SEÇÕES
// --------------------------------------------
const items = [MobileCartton, MobileSereia, NemoBanner, MobileSereia];
const channels = [Star, Geographic, Pixar, Marvel, StarWars, Disney];


// --------------------------------------------
//  SWIPER CONFIGS
// --------------------------------------------
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

const proximos: MediaItem[] = [

    {
        id: 115,
        title: "CHIP",
        image: Chip,
        modalImage: modalChip,
        youtubeUrl:
            "https://www.youtube.com/embed/oYyjB7eROPg?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Tico e Teco vivem entre desenhos animados e humanos na Los Angeles moderna, mas suas vidas são bem diferentes agora. Um dia, um ex-colega de elenco desaparece misteriosamente, então a dupla precisa reparar sua amizade quebrada e salvar o amigo.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 116,
        title: "Duck",
        image: Duck,
        modalImage: modalDuck,
        youtubeUrl:
            "https://www.youtube.com/embed/lcpCapjKT9I?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "DuckTales (ou DuckTales: Os Caçadores de Aventuras) acompanha o Tio Patinhas, o pato mais rico do mundo, que, após o Pato Donald se juntar à Marinha, assume a guarda de seus sobrinhos trigêmeos Huguinho, Zezinho e Luizinho, embarcando com eles em emocionantes aventuras globais em busca de tesouros lendários e para proteger sua vasta fortuna dos vilões, especialmente os Irmãos Metralha e o MacMônei. ",
        tags: ["Animação", "Disney", "Aventura Épica"]
    },
    {
        id: 119,
        title: "MsMarvel",
        image: verticalMsMarvel,
        modalImage: modalMsMarvel,
        youtubeUrl:
            "https://www.youtube.com/embed/tz9ghPTmyN4?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 35min",
        rating: "Livre",
        genre: ["Comédia", "Fantasia", "Família"],
        description:
            "Kamala Khan, uma adolescente muçulmana gamer e fã de super-heróis (especialmente a Capitã Marvel) de Jersey City, que se sente deslocada, mas vê sua vida mudar ao ganhar superpoderes cósmicos, tendo que equilibrar sua vida normal com sua nova identidade de heroína, tudo isso enquanto explora sua cultura e laços familiares.",
        tags: ["Pixar", "Amizade", "Família"],
    },
    {
        id: 117,
        title: "Kenobi - Wan",
        image: Kenobi,
        modalImage: modalWan,
        youtubeUrl:
            "https://www.youtube.com/embed/YseHkkLPzjs?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Obi-Wan Kenobi (Disney+) foca no exílio do Mestre Jedi Obi-Wan Kenobi em Tatooine, uma década após a queda de Anakin Skywalker para o Lado Sombrio, transformando-o em Darth Vader, com a missão de proteger um jovem Luke Skywalker enquanto lida com a perseguição do Império e confronta seu passado, enfrentando inimigos e a própria culpa, numa jornada que o reconecta à Força e ao destino da galáxia.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

    {
        id: 118,
        title: "CHERELLA - KERELLA",
        image: Sneak,
        modalImage: modalKerella,
        youtubeUrl:
            "https://www.youtube.com/embed/Qgg_11ISxu8?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Em meio à inovadora cultura de rua de Nova York, 'Os Tênis Encantados' é um filme repleto de adrenalina e música que traz uma versão contemporânea do conto de fadas 'Cinderela'. El é um aspirante a designer de tênis que trabalha no estoque da loja de calçados da sua falecida mãe. Ele esconde seu talento artístico do padrasto e de dois meios-irmãos mesquinhos, que sempre estragam qualquer oportunidade que aparece para ele. Até que El conhece Kira King, a filha independente de Darius King, lenda do basquete e magnata dos tênis. Com o incentivo da melhor amiga e um toque de magia, El cria coragem para usar seu talento e correr atrás do sonho de virar um designer de verdade no ramo dos tênis. Contém sequências de luzes que podem afetar pessoas fotossensíveis.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    }
]
register(...proximos);

const comedy: MediaItem[] = [
    getMedia(107)!, // Nate
    getMedia(101)!, // West Side Story
    getMedia(115)!, // CHIP
    {
        id: 114,
        title: "Encanto",
        image: Encanto,
        modalImage: modalEncanto,
        youtubeUrl:
            "https://www.youtube.com/embed/Ksji3ZXcu9E?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Olivia Rodrigo: Dirigindo até Você (Disney+) foca na criação do álbum SOUR, com a cantora viajando de Salt Lake City, compartilhando memórias e emoções sobre seu sucesso e vida.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    {
        id: 120,
        title: "Era do Gelo",
        image: Icev,
        modalImage: modalIce,
        youtubeUrl:
            "https://www.youtube.com/embed/rVQelqH7dH4?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Vinte mil anos atrás, num mundo coberto de gelo, o mamute Manfred e a preguiça Sid resgatam um bebê humano órfão. Agora, os dois vão enfrentar muitas aventuras até devolver o filhote de gente à sua tribo, que migrou para um novo acampamento.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
     {
        id: 121,
        title: "Liga da Justiça",
        image: Zack,
        modalImage: modalJustice,
        youtubeUrl:
            "https://www.youtube.com/embed/BZUm2lpPoKM?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Impulsionado pela restauração de sua fé na humanidade e inspirado pelo ato altruísta do Superman, Bruce Wayne convoca sua nova aliada Diana Prince para o combate contra um inimigo ainda maior, recém-despertado. Juntos, Batman e Mulher-Maravilha buscam e recrutam com agilidade um time de meta-humanos, mas mesmo com a formação da liga de heróis sem precedentes, pode ser tarde demais para salvar o planeta de um catastrófico ataque.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },

]
register(...comedy);

const action: MediaItem[] = [
    getMedia(121)!,//liga da justiça
    {
        id: 121,
        title: "Maze Runner",
        image: Run,
        modalImage: modalRun,
        youtubeUrl:
            "https://www.youtube.com/embed/BZUm2lpPoKM?controls=1&modestbranding=1&rel=0&showinfo=0&playsinline=1&autoplay=1&mute=1",
        year: 2021,
        duration: "1h 57min",
        rating: "10",
        genre: ["Aventura", "Fantasia", "Família"],
        description:
            "Impulsionado pela restauração de sua fé na humanidade e inspirado pelo ato altruísta do Superman, Bruce Wayne convoca sua nova aliada Diana Prince para o combate contra um inimigo ainda maior, recém-despertado. Juntos, Batman e Mulher-Maravilha buscam e recrutam com agilidade um time de meta-humanos, mas mesmo com a formação da liga de heróis sem precedentes, pode ser tarde demais para salvar o planeta de um catastrófico ataque.",
        tags: ["Animação", "Disney", "Aventura Épica"],
    },
    John,
    Iron,
    This,
    Faye
]


// --------------------------------------------
//  MODAL LOGIC
// --------------------------------------------
const modalOpen = ref(false);
const modalItem = ref<MediaItem | null>(null);
const loading = ref(false);
const showVideo = ref(false);

function onImageLoaded() {
    loading.value = false;
}

async function openModal(params) {
    const functionItem = params.item;
    loading.value = true;
    showVideo.value = false;
    modalItem.value = null;
    modalOpen.value = true;

    modalItem.value = functionItem;

    const img = new Image();
    img.src = functionItem.modalImage;

    img.onload = () => loading.value = false;
    img.onerror = () => {
        console.error("Erro ao carregar a imagem do modal.");
        loading.value = false;
    };
}

function playVideo() {
    showVideo.value = true;
}

function close() {
    modalOpen.value = false;
    showVideo.value = false;
    modalItem.value = null;
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
            <MoleculeBodyCarousel :items="newPrograms" @slide-click="openModal" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item.image" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>

        </div>
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Próximos
            </h2>
            <MoleculeBodyCarousel :items="proximos" @slide-click="openModal" :swiperOptions="swiperBodyConfig">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[405px]">
                        <img :src="item.image" class="w-full h-full object-cover rounded-xl" />
                    </div>

                </template>
            </MoleculeBodyCarousel>
        </div>
        <div class="new pl-4 pr-4">
            <h2 class="text-start sm:mb-[40px]">
                Comédia
            </h2>
            <MoleculeBodyCarousel :items="comedy" :swiperOptions="swiperBodyConfig" @slide-click="openModal">
                <template #slide="{ item }">
                    <div class="w-[120px] h-[180px] sm:w-[290px] sm:h-[165px]">
                        <img :src="item.image" class="w-full h-full object-cover rounded-xl" />
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
            <div v-else class="p-4 flex flex-col items-center gap-4 justify-center">
                <img :src="modalItem?.modalImage"
                    class="rounded-xl object-contain relative hover:brightness-[0.1] transition-all duration-500 max-h-[80vh]" />
                <AtomButtonPlay class="absolute cursor-pointer top-[50%] bg-white" label="PLAY" :icon="playIcon"
                    size="md" variant="default" @click="playVideo" />
                <button class="absolute right-3 top-3 text-zinc-700 hover:text-black" @click="close"
                    aria-label="Fechar">
                    ✕
                </button>
                <p class="text-center font-bold w-[800px] text-base absolute top-[60%]">
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
