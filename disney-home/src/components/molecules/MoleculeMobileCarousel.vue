<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import "swiper/css/autoplay"; // IMPORTANTE
import { Pagination, FreeMode, Autoplay } from "swiper/modules";

const props = defineProps({
    items: Array,
    swiperOptions: Object,
});
</script>

<template>
    <div class="w-full">
        <Swiper
            :modules="[Pagination, FreeMode, Autoplay]"
            v-bind="swiperOptions"
            class="w-full h-[200px]"
        >
            <SwiperSlide
                v-for="(item, index) in items"
                :key="index"
                class="flex items-center justify-center rounded-xl overflow-hidden"
            >
                <slot name="slide" :item="item" :index="index">
                    <img :src="item" class="w-full h-40 object-cover rounded-xl" />
                </slot>
            </SwiperSlide>

            <div class="swiper-pagination"></div>
        </Swiper>
    </div>
</template>

<style scoped>
:deep(.swiper-pagination-bullet) {
   display:none;
}
</style>
