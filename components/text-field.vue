<template>
    <div class="form-floating mb-3">
        <input
            :value="modelValue"
            :type="typeInput"
            :placeholder="placeholder"
            class="form-control"
            :id="`${label}-floatingInputValue`"
            required
            @input="$emit('update:modelValue', $event.target.value)"
        >
        <label for="floatingInputGrid">{{ label }}</label>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    props: {
        typeInput: {
            type: String,
            default: 'text',
        },
        modelValue: {
            type: String,
            default: '',
        },
        placeholder: {
            type: String,
            default: '',
        },
        label: {
            type: String,
            default: '',
        },
    },
    emits: ['update:modelValue'],
});
</script>

