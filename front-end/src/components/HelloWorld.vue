<script setup>
import { ref } from "vue";

const count = ref(0);
function test() {
  count.value++;
}
</script>

<template>
  {{ count }}
  <span @click="test">Count is: {{ count }}</span>
</template>
