<template>
    <div>
      <div class="mt-[8rem] md:mx-[24rem] mx-8 md:h-[22rem] h-[22rem] md:w-[30rem] rounded-lg bg-gradient-to-r to-red-600 from-yellow-500">
        <form @submit.prevent="register">
          <h1 class="text-2xl text-center mb-4 mt-4 font-medium">Create an account</h1>
    
          <!-- For error -->
          <div v-if="error" class="mx-6 p-2 px-4 bg-red-600 mb-2 w-[90%] rounded-md">
            {{ error }}
          </div>

          <!-- <label for="email">Username</label> -->
          <input class="mb-6 mx-6 p-2 px-4 w-[90%] rounded-md md:text-sm text-xs" v-model="username" required placeholder="Username" id="username"/>
    
          <!-- <label for="email">Email</label> -->
          <input class="mb-6 mx-6 p-2 px-4 w-[90%] rounded-md md:text-sm text-xs" v-model="email" required placeholder="Email" id="email"/>
    
          <!-- <label for="password">Password</label> -->
          <div class="flex">
            <input class="mb-4 mx-6 p-2 px-4 w-[90%] rounded-md md:text-sm text-xs" v-model="passOne" required placeholder="Password" type="password"/>
            <input class="mb-4 mx-6 p-2 px-4 w-[90%] rounded-md md:text-sm text-xs" v-model="passTwo" required placeholder="Confirm Password" type="password"/>
          </div>

          <div class="flex mx-6 mb-4">
            <span class="text-sm mx-2">Already have an account? </span> 
            <router-link class="text-sm text-white" to="/login">Sign in</router-link>
          </div>
    
          <div class="mx-4 text-center">
            <button class="border p-2 px-10 text hover:text-white rounded-md text-sm" type="submit">Register</button>
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
        username: null,
        passOne: null,
        passTwo: null,
        error: null
      }
    },
  
    methods: {
      register: function() {
        // objects that have both email and password
        const info = {
          email: this.email,
          password: this.passTwo,
          username: this.username
        }

        if(!this.error) {

        }
  
        // Authenticate 
        firebase.auth()
        .createUserWithEmailAndPassword(info.email, info.passOne)
        .then(() => {
          userCredentials => {
            return userCredentials.user.updateProfile({
                username: info.username
            }).then(() => {
                this.$router.replace('/')
            })
          }
        }, error => {
          this.error = error.message
        })
      }
    },

    watch: {
        // To watch the second pass
        passTwo: function() {
            if(this.passOne !== '' && this.passTwo !== '' && this.passTwo !== this.passOne) {
                this.error = 'Password do not match'
            } else {
                this.error = null
            }
        }
    }
  }
  </script>
  