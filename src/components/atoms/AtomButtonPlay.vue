<!-- src/atoms/AtomButton.vue -->
<script setup lang="ts">
import { defineProps, computed, PropType } from "vue";

const props = defineProps({
    label: {
        type: String,
        default: "Button",
    },

    // AGORA aceita componente OU string (URL)
    icon: {
        type: [Object, String] as PropType<Record<string, any> | string>,
        default: null,
    },

    iconPosition: {
        type: String as PropType<"left" | "right">,
        default: "left",
    },

    disabled: {
        type: Boolean,
        default: false,
    },

    loading: {
        type: Boolean,
        default: false,
    },

    size: {
        type: String as PropType<"sm" | "md" | "lg">,
        default: "md",
    },

    variant: {
        type: String as PropType<"default" | "ghost" | "outline">,
        default: "default",
    },

    block: {
        type: Boolean,
        default: false,
    },
});

const classes = computed(() => {
    const base =
        "inline-flex items-center justify-center gap-2 rounded-md font-medium transition-all select-none";

    const sizes: Record<string, string> = {
        sm: "text-xs px-2 py-1",
        md: "text-sm px-3 py-2",
        lg: "text-base px-4 py-3",
    };

    const variants: Record<string, string> = {
        default: "bg-black text-black hover:bg-zinc-800",
        ghost: "bg-transparent hover:bg-zinc-200",
        outline: "border border-black hover:bg-zinc-100",
    };

    const cursor =
        props.disabled || props.loading
            ? "opacity-50 cursor-not-allowed"
            : "cursor-pointer";

    const width = props.block ? "w-full" : "";

    return [
        base,
        sizes[props.size],
        variants[props.variant],
        cursor,
        width,
    ].join(" ");
});
</script>

<template>
    <button :class="classes" :disabled="disabled || loading">

        <!-- Ícone esquerda -->
        <span v-if="icon && !loading && iconPosition === 'left'">
            <!-- Se for componente -->
            <component v-if="typeof icon === 'object'" :is="icon" />

            <!-- Se for string (URL) -->
            <img v-else :src="icon" class="w-5 h-5 object-contain" alt="icon" />
        </span>

        <!-- Label ou loading -->
        <span>{{ loading ? "..." : label }}</span>

        <!-- Ícone direita -->
        <span v-if="icon && !loading && iconPosition === 'right'">
            <component v-if="typeof icon === 'object'" :is="icon" />
            <img v-else :src="icon" class="w-5 h-5 object-contain" alt="icon" />
        </span>

    </button>
</template>

<style scoped>
button {
    line-height: 1;
}
</style>
