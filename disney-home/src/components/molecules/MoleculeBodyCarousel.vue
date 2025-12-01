<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/scrollbar";
import "swiper/css/autoplay";
import { ref } from "vue";
import type { Swiper as SwiperType } from "swiper";

import { Scrollbar, Autoplay, FreeMode } from "swiper/modules";

// Tipagem CORRETA dos props
const props = defineProps<{
    items: string[];
    swiperOptions?: Record<string, any>;
}>();

// Instância do Swiper
const swiperInstance = ref<SwiperType | null>(null);
</script>

<template>
    <div class="w-full">
        <Swiper :modules="[Scrollbar, Autoplay, FreeMode]" v-bind="props.swiperOptions" class="w-full h-full"
            @swiper="swiperInstance = $event" @mouseenter="swiperInstance?.autoplay?.stop()"
            @mouseleave="swiperInstance?.autoplay?.start()">
            <SwiperSlide v-for="(item, index) in props.items" :key="index"
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

<style scoped></style>
