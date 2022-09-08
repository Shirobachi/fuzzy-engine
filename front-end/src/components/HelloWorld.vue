<script setup>

import { ref } from 'vue'

defineProps({
  msg: String
})
var awesome = ref(true)
const count = ref(0)
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

  <div>
      <h2>Sign up</h2>
      
      <p>
        <input for="email" type="email" placeholder="email" required v-model="email" @blur="validateEmail" />
      </p>
      <p class="text-red-500" v-if="email.length == 0">E-mail cant be empty</p>
      <p>
        <input type="password"  v-model="password" placeholder="password" />
      </p>
      <p class="error-message" v-show="password.length < 6">The password must be at least 6 characters</p>
  </div>
  <div>
    <p v-if="active">Using v-if</p>
    <p v-show="active">Using v-show</p>
    <button @click="active = !active">Toggle active</button>
  </div>

  </div>
</section>
</template>

<script>
  export default {
  data() {
    return {
      email: '',
      password: '',
      active: false,
    }
  },
/*   methods: {
    validateEmail(email) {
      if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(this.email)) {
        this.msg['email'] = 'Please enter a valid email address';
    } else {
        this.msg['email'] = '';
    }
    },
  }, */
  
}
</script>

