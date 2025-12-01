<script setup lang="ts">
const props = defineProps<{
    items: string[]
}>();
</script>

<template>
    <div v-bind="$attrs">
        <div v-for="channel in props.items" :key="channel">
            <slot name="channel">
                <img class="max-w-[110px] sm:max-w-[185px]" :src="channel" alt="" />
            </slot>
        </div>
    </div>
</template>

<style></style>
