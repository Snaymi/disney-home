<!-- src/atoms/AtomButton.vue -->
<script setup lang="ts">
import { defineProps, computed } from "vue";

const props = defineProps({
    label: {
        type: String,
        default: "Button",
    },
    icon: {
        type: Object, // Componente Vue (SVG)
        default: null,
    },
    iconPosition: {
        type: String as () => "left" | "right",
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
        type: String as () => "sm" | "md" | "lg",
        default: "md",
    },
    variant: {
        type: String as () => "default" | "ghost" | "outline",
        default: "default",
    },
    block: {
        type: Boolean,
        default: false,
    }
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
        default: "bg-black text-white hover:bg-zinc-800",
        ghost: "bg-transparent hover:bg-zinc-200",
        outline: "border border-black hover:bg-zinc-100",
    };

    const cursor = props.disabled || props.loading ? "opacity-50 cursor-not-allowed" : "cursor-pointer";

    const width = props.block ? "w-full" : "";

    return [base, sizes[props.size], variants[props.variant], cursor, width].join(" ");
});
</script>

<template>
    <button :class="classes" :disabled="disabled || loading">
        <span v-if="icon && !loading && iconPosition === 'left'">
            <component :is="icon" />
        </span>

        <span>{{ loading ? "..." : label }}</span>

        <span v-if="icon && !loading && iconPosition === 'right'">
            <component :is="icon" />
        </span>
    </button>
</template>

<style scoped>
button {
    line-height: 1;
}
</style>
