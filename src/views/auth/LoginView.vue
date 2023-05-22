<template>
  <div>
    <div class="mt-[8rem] md:mx-[24rem] mx-8 md:h-[22rem] md:w-[30rem] rounded-lg bg-gradient-to-r to-red-600 from-yellow-500">
      <form @submit.prevent="handleLogin">
        <h1 class="text-2xl text-center mb-4 mt-4 font-medium">Log in</h1>
  
        <!-- For error -->
        <div v-if="error" class="mx-6 p-2 px-4 bg-red-600 mb-2 w-[90%] rounded-md">
          {{ error }}
        </div>
        <!-- <label for="email">Email</label> -->
        <input class="mb-6 mx-6 p-2 px-4 w-[90%] rounded-md" v-model="email" required placeholder="Email" id="email"/>
  
        <!-- <label for="password">Password</label> -->
        <input class="mb-4 mx-6 p-2 px-4 w-[90%] rounded-md" v-model="password" required placeholder="Password" type="password"/>

        <div class="flex mx-6 mb-4">
          <span class="text-sm mx-2">Don't have an account? </span> 
          <router-link class="text-sm text-white" to="/register">Register</router-link>
        </div>
  
        <div class="mx-4 text-center">
          <button class="border p-2 px-10 text hover:text-white rounded-md" type="submit">Log in</button>
        </div>
      </form>
    </div>

  </div>
</template>

<script>
import firebase from 'firebase/compat/app'
import 'firebase/compat/auth';

export default {
  data: function() {
    return {
      email: null,
      password: null,
      error: null
    }
  },

  methods: {
    handleLogin: function() {
      // objects that have both email and password
      const info = {
        email: this.email,
        password: this.password
      }

      // Authenticate 
      firebase.auth()
      .signInWithEmailAndPassword(info.email, info.password)
      .then(() => {
        this.$router.push('/')
      }, error => {
        this.error = error.message
      })
    }
  }
}
</script>
