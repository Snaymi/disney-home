<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";

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
        <Swiper v-bind="swiperOptions" class="w-full h-64">
            <SwiperSlide v-for="(item, index) in items" :key="index" class="!h-64">
                <slot name="slide" :item="item" :index="index" />
            </SwiperSlide>
        </Swiper>
    </div>
</template>
