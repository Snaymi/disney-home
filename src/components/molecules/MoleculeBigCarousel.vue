<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay";
import { ref } from "vue";
import type { Swiper as SwiperType } from "swiper";
import { Autoplay } from "swiper/modules";

// 🔥 Tipagem correta
const props = defineProps<{
    items: string[];
    swiperOptions?: Record<string, any>;
}>();

const swiperInstance = ref<SwiperType | null>(null);
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Autoplay]" v-bind="props.swiperOptions" class="w-full h-64" @swiper="swiperInstance = $event"
            @mouseenter="swiperInstance?.autoplay?.stop()" @mouseleave="swiperInstance?.autoplay?.start()">
            <SwiperSlide v-for="(item, index) in props.items" :key="index" class="!h-[180px]">
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
