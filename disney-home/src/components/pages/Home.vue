<!-- src/pages/HomePage.vue -->
<script setup>
import Header from "../organisms/Header.vue";
import "../../style.css"; // variáveis globais
import OrganismBody from "../organisms/OrganismBody.vue";
</script>

<template>
    <div class="bg-(--header)">
        <Header />
    </div>

    <OrganismBody />
</template>

<style scoped></style>
