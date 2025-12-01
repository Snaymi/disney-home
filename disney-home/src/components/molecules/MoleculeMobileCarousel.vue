<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination, FreeMode, Autoplay } from "swiper/modules";

const props = defineProps<{
    items: string[];
    swiperOptions?: Record<string, any>;
}>();
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Pagination, FreeMode, Autoplay]" v-bind="props.swiperOptions" class="w-full h-[200px]">
            <SwiperSlide v-for="(item, index) in props.items" :key="index"
                class="flex items-center justify-center rounded-xl overflow-hidden">
                <slot name="slide" :item="item" :index="index">
                    <img :src="item" class="w-full h-40 rounded-xl" />
                </slot>
            </SwiperSlide>

            <div class="swiper-pagination"></div>
        </Swiper>
    </div>
</template>

<style scoped>
:deep(.swiper-pagination-bullet) {
    display: none;
}
</style>
