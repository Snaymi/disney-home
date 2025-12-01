<script lang="ts" setup>
// import { Logo } from "../atoms"
import {Logo,
    Profile
} from "../atoms";


</script>


<template>
    <div class="flex gap-y-3 mt-3 p-3 flex-col justify-center items-center">
        <div class="flex items-center justify-center gap-x-[70px] xl:hidden">
            <img class="w-[25px]" src="../../assets/img/icon/house.svg" alt="">
            <img class="w-[25px]" src="../../assets/img/icon/search.svg" alt="">
            <img class="w-[25px]" src="../../assets/img/icon/Download.svg" alt="">
            <Profile class="w-[25px]"/>
        </div>
        <div class="hidden lg:block">
            <Logo />
        </div>
        <div class="hidden xl:flex justify-center items-center gap-x-5 text-xs">
            <p>Política de Privacidade</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
            <p>Acordo de Inscrição</p>
        </div>
        <div class="hidden lg:block">
            °DISNEY
        </div>
    </div>

</template>



<style lang="scss" scoped></style>