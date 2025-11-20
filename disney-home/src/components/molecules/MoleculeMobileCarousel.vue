<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";

// CSS do Swiper
import "swiper/css";
import "swiper/css/pagination";
import { Pagination, FreeMode } from "swiper/modules";

const props = defineProps({
    items: {
        type: Array as () => Array<any>,
        default: () => [],
    },
    swiperOptions: {
        type: Object,
        default: () => ({}),
    },
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Pagination, FreeMode]" v-bind="swiperOptions" class="w-full h-40">
            <SwiperSlide v-for="(item, index) in items" :key="index"
                class="flex items-center justify-center bg-neutral-700 rounded-lg !h-40">
                <slot name="slide" :item="item" :index="index">
                    <!-- fallback -->
                    <img :src="item" alt="mobile-slide" class="w-full h-full object-cover rounded-lg" />
                </slot>
            </SwiperSlide>

            <!-- Pagination -->
            <div class="swiper-pagination"></div>
        </Swiper>
    </div>
</template>
