<script setup lang="ts">
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/autoplay";
import { ref } from "vue";
import type { Swiper as SwiperType } from "swiper";
import { Autoplay } from "swiper/modules";

const props = defineProps<{
    items: MediaItem[];
    swiperOptions?: Record<string, any>;
}>();

const emit = defineEmits<{
    (e: "slide-click", payload: { item: MediaItem; index: number }): void;
}>();

const swiperInstance = ref<SwiperType | null>(null);

function stopAutoplay() {
    swiperInstance.value?.autoplay?.stop?.();
}
function startAutoplay() {
    swiperInstance.value?.autoplay?.start?.();
}
</script>

<template>
    <div class="w-full" @mouseenter="stopAutoplay" @mouseleave="startAutoplay">
        <Swiper :modules="[Autoplay]" v-bind="props.swiperOptions" class="w-full h-64"
            @swiper="swiperInstance = $event">
            <SwiperSlide v-for="(item, index) in props.items" :key="item.id" class="cursor-pointer !h-[180px]"
                @click="emit('slide-click', { item, index })">
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
