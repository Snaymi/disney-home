<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
import { Pagination, FreeMode } from "swiper/modules";

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
        <Swiper
            :modules="[Pagination, FreeMode]"
            v-bind="swiperOptions"
            class="w-full h-[200px]"
        >
            <!-- AGORA SIM: LOOP CORRETO -->
            <SwiperSlide
                v-for="(item, index) in items"
                :key="index"
                class="flex items-center justify-center rounded-xl overflow-hidden "
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
:deep(.swiper) {
    padding-bottom: 20px;
}
:deep(.swiper-pagination-bullet) {
   display:none;
}
:deep(.swiper-pagination-bullet-active) {
    display: none;
}
:deep(.swiper-slide) {
    border-radius: 14px;
    overflow: hidden;
}
</style>
