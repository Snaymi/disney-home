<!-- src/molecules/MoleculeModal.vue -->
<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from "vue";

const props = defineProps({
    modelValue: { type: Boolean, required: true } // v-model
});
const emit = defineEmits(["update:modelValue"]);


function close() {
    emit("update:modelValue", false);
}

function onKey(e: KeyboardEvent) {
    if (e.key === "Escape") close();
}

onMounted(() => window.addEventListener("keydown", onKey));
onBeforeUnmount(() => window.removeEventListener("keydown", onKey));
</script>

<template>
    <teleport to="body">
        <div v-if="modelValue" class="fixed inset-0 z-50 flex items-center justify-center">
            <!-- overlay -->
            <div class="absolute inset-0 bg-black/60" @click="close" aria-hidden="true" />
            <!-- modal content -->
            <div role="dialog" aria-modal="true"
                class="relative z-10 bg-white dark:bg-zinc-900 rounded-2xl shadow-2xl p-1">

                <div>
                    <slot />
                </div>
            </div>
        </div>
    </teleport>
</template>

<style scoped>
/* pequena suavização */
</style>
