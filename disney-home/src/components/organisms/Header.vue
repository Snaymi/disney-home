<template>
    <div class="header-content p-6">
        <div class="content flex justify-between  items-center ">
            <div class="w-full flex justify-center sm:justify-around gap-x-15">
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