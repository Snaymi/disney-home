<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay";


import { Autoplay } from "swiper/modules";

const props = defineProps({
    items: Array,
    swiperOptions: Object,
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Autoplay]" v-bind="swiperOptions" class="w-full h-64">
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
