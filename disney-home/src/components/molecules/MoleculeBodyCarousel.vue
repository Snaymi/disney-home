<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/scrollbar";

import { Scrollbar } from "swiper/modules";

const props = defineProps({
    items: { type: Array, required: true },
    swiperOptions: { type: Object, default: () => ({}) }
});
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Scrollbar]" v-bind="swiperOptions" class="w-full h-full">
            <SwiperSlide v-for="(item, index) in items" :key="index"
                class="!flex !justify-center !items-center bg-gray-800 text-white">
                <slot name="slide" :item="item" :index="index">
                    <div class="w-full h-full flex items-center justify-center text-lg font-semibold">
                        {{ item }}
                    </div>
                </slot>
            </SwiperSlide>

            <template #container-end>
                <div class="swiper-scrollbar"></div>
            </template>
        </Swiper>
    </div>
</template>

<style scoped>
.swiper-slide {
  width: 120px !important;
}
</style>
