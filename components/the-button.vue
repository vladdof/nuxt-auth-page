<template>
    <button class="btn btn-primary" type="button" :disabled="isLoading">
      <span v-if="isLoading" class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span>
      {{ buttonText }}
    </button>
</template>


<script lang="ts">
import { defineComponent, computed } from 'vue';

export default defineComponent({
    props: {
        text: {
            type: String,
            required: true,
        },
        isLoading: {
            type: Boolean,
            default: false,
        },
    },
    setup(props) {
        const buttonText = computed(() => (props.isLoading ? 'Loading...' : props.text));

        return {
            buttonText,
        };
    },
});
</script>

