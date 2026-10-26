<script setup>
import {ref, onMounted} from 'vue'

const message = ref('loading...');
const error = ref('');

onMounted(async () => {
  try {
    const response = await fetch('api/hello/');
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const data = await response.json();
    message.value = data.message;
  } catch (err) {
    error.value = `Failed to fetch message: ${err instanceof Error ? err.message : String(err)}`;
  }
});

</script>

<template>
  <main>
    <h1>Vue + Django</h1>
    <p v-if="!error">{{ message }}</p>
    <p v-else class="error">{{ error }}</p>
  </main>
</template>
<style scoped>
main{
  text-align: center;
  margin-top: 50px;
}
.error{
  color: red;
}
</style>