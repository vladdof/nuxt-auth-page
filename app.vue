<template>
  <div class="container-fluid vh-100 py-3">
    <div class="row h-100 justify-content-center align-items-center">
      <div class="col col-md-6">
        <div class="container">
          <spinner v-if="loading" />
          <div v-else>
            <NuxtPage />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import { delay } from './lib/delay';

export default defineComponent({
  setup() {
    const loading = ref(true);

    onMounted(() => {
      delay()
        .then(() => {
          loading.value = false;
        })
        .catch((error) => {
          console.error(error);
          loading.value = false;
        });
    });

    return {
      loading,
    };
  },
})
</script>
