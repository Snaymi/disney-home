<template>
    <div class="header-content h-[50px] flex items-center justify-center sm:h-auto sm:block p-6">
        <div class="content flex justify-between  items-center">
            <div class="w-full flex justify-center sm:justify-start gap-x-15">
                <HeaderLeft />
                <HeaderMiddle />
            </div>
            <HeaderRight />
        </div>
    </div>

</template>

<script setup>
import HeaderLeft from '../molecules/HeaderLeft.vue';
import HeaderMiddle from '../molecules/HeaderMiddle.vue';
import HeaderRight from '../molecules/HeaderRight.vue';

</script>

<style lang="scss" scoped>

</style>