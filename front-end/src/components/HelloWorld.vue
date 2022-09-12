<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});
var awesome = ref(true);
const count = ref(0);

const header = ref("To do list");
const tasks = ref([
  { id: 1, text: "Learn Vue", done: true },
  { id: 2, text: "Learn React", done: false },
  { id: 3, text: "Learn Angular", done: false },
]);
const newTask = ref("");
const highPiority = ref(false);
</script>

<template>
  <section>
    <h1>{{ msg }}</h1>

    <div class="flex flex-col space-y-4">
      <button type="button" class="bg-red-800 mt-6" @click="count++">
        count is {{ count }}
      </button>

      <button type="button" class="bg-blue-800" @click="awesome = !awesome">
        Click
      </button>
      <h1 v-if="awesome">Beacuse programming is my biggest passion!</h1>
      <h1 v-else>Just joking, I hate it 😢</h1>
      <h2 v-if="count > 10">You clicked more than 10 times!</h2>
      <h2 v-else>You haven't clicked more than 10 times!</h2>

      <div>
        <h2>Sign up</h2>

        <p>
          <input
            for="email"
            type="email"
            placeholder="email"
            required
            v-model="email"
            @blur="validateEmail" />
        </p>
        <p class="text-red-500" v-if="email.length == 0">
          E-mail cant be empty
        </p>
        <p>
          <input type="password" v-model="password" placeholder="password" />
        </p>
        <p class="error-message" v-show="password.length < 6">
          The password must be at least 6 characters
        </p>
      </div>
      <div>
        <p v-if="active">Using v-if</p>
        <p v-show="active">Using v-show</p>
        <button @click="active = !active">Toggle active</button>
      </div>

      <form
        v-on:submit.prevent="
          tasks.push({ id: tasks.length + 1, text: newTask })
        "
        class="rounded-md border-4 border-emerald-400">
        <h1
          class="m-8 rounded-md border-4 border-lime-500 font-sans font-semibold text-2xl italic">
          {{ header }}
        </h1>
        <input
          v-model="newTask"
          type="text"
          @keyup.enter="addTask"
          placeholder="Add task"
          class="placeholder:italic placeholder-amber-50 rounded-md text-center border-8 border-purple-900" />
        <label>
          <input
            v-model="highPiority"
            type="checkbox"
            class="ml-6 checked:bg-green-500 indeterminate:bg-red-600 default:ring-2" />
          High priority
        </label>
        <div class="qmt-8 flex justify-center items-center">
            <button
            class="flex relative justify-center p-0.5 mb-2 mr-2 overflow-hidden text-sm font-medium text-gray-900 rounded-lg group bg-gradient-to-br from-green-400 to-blue-600 group-hover:from-green-400 group-hover:to-blue-600 hover:text-white dark:text-white focus:ring-4 focus:outline-none focus:ring-green-200 dark:focus:ring-green-800">
            <span
            class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white dark:bg-gray-900 rounded-md group-hover:bg-opacity-0">
            Save task
        </span>
    </button>
</div>

        <ul class="m-4">
          <li v-for="{ id, text } in tasks" :key="id">
            {{ text }}
          </li>
        </ul>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      active: false,
    };
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
};
</script>
