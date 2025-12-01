<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay";
import { ref } from "vue";
import type { Swiper as SwiperType } from 'swiper';

import { Autoplay } from "swiper/modules";

const swiperInstance = ref<SwiperType | null>(null);
const props = defineProps({
    items: Array,
    swiperOptions: Object,
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Autoplay]" v-bind="swiperOptions" class="w-full h-64" @swiper="swiperInstance = $event"
            @mouseenter="swiperInstance?.autoplay?.stop()" @mouseleave="swiperInstance?.autoplay?.start()">
            <SwiperSlide :modules="[Autoplay]" class="!h-[180px]" v-for="(item, index) in items" :key="index">
                <slot name="slide" :item="item" :index="index" />
            </SwiperSlide>
        </Swiper>
    </div>
</template>

<style>
.swiper-slide {
    background-color: transparent;
}
</style>
