<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay"; // IMPORTANTE
import { Autoplay } from "swiper/modules";

const props = defineProps({
    items: Array,
    swiperOptions: Object,
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Autoplay]" v-bind="swiperOptions" class="w-full h-64">
            <SwiperSlide v-for="(item, index) in items" :key="index" class="!h-64">
                <slot name="slide" :item="item" :index="index" />
            </SwiperSlide>
        </Swiper>
    </div>
</template>
