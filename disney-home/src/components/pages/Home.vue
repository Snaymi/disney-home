<!-- src/pages/HomePage.vue -->
<script setup>
import "../../style.css"; // variáveis globais
import {
    OrganismBody,
    Header,
    Footer
} from "../organisms"
</script>

<template>

    <div class="bg-(--body) flex flex-col gap-y-5">
        <div class="bg-(--header)">
            <Header />
        </div>

        <div>
            <OrganismBody />
        </div>

        <div class="bg-(--footer)">
            <Footer />
        </div>
    </div>

</template>

<style scoped></style>
