<script setup>
import { ref } from 'vue';
import VueGuide from './VueGuide.vue';

defineProps({
  msg: String
})

</script>

<template>
  <h1>{{ msg }}</h1>
  <VueGuide />
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
