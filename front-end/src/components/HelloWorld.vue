<script setup>

import { ref } from 'vue'

defineProps({
  msg: String
})
var awesome = ref(true)
const count = ref(0)
<script src="https://unpkg.com/vue-router@4"></script>
</script>

<template>
<section>
  <h1>{{ msg }}</h1>

  <div class="flex flex-col space-y-4">
    <button type="button" class="bg-red-800 mt-6" @click="count++">count is {{ count }}</button>
    
    <button type="button" class="bg-blue-800" @click="awesome = !awesome">Click</button>
    <h1 v-if="awesome">Beacuse programming is my biggest passion!</h1>
    <h1 v-else>Just joking, I hate it 😢</h1>
    <h2 v-if="count > 10">You clicked more than 10 times!</h2>
    <h2 v-else>You haven't clicked more than 10 times!</h2>    
  </div>
</section>
</template>

