<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/scrollbar";
import "swiper/css/autoplay"
import { ref } from "vue";
import type { Swiper as SwiperType } from 'swiper';

const swiperInstance = ref<SwiperType | null>(null);

import { Scrollbar, Autoplay, FreeMode } from "swiper/modules";

const props = defineProps({
    items: { type: Array, required: true },
    swiperOptions: { type: Object, default: () => ({}) }
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Scrollbar, Autoplay, FreeMode]" v-bind="swiperOptions" class="w-full h-full"
        @swiper="swiperInstance=$event"
        @mouseenter="swiperInstance?.autoplay?.stop()"
        @mouseleave="swiperInstance?.autoplay?.start()">
            <SwiperSlide v-for="(item, index) in items" :key="index"
                class="!flex !justify-center !items-center bg-gray-800 text-white !w-[120px] sm:!w-[290px]">
                <slot name="slide" :item="item" :index="index">
                    <div class="w-full h-full flex items-center justify-center text-lg font-semibold">
                        {{ item }}
                    </div>
                </slot>
            </SwiperSlide>
        </Swiper>
    </div>
</template>

<style scoped>

</style>
