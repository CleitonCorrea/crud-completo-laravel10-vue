<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <p class="text-center">Desenvolvido por @Cleiton Corrêa</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
