<template>
  <div class="mt-3">
    <div class="text-center font-medium">
      Welcome to DOOM <span class="text-gray-500">{{ user }}</span>
    </div>

    <div class="text-center font-bold">
      <h1 class="mb-4 text-4xl">Video Chat</h1>

      <p class="font-normal md:mx-[30rem] mx-[14rem] text-sm w-[14rem] mb-4">
        This app uses firebase for real time communication and webRTC to create
        video chat's between users, allowing you to create rooms for your meetings and invite atendees.
      </p>

        <router-link class="font-normal mx-4 p-2 px-4 border text-xs rounded-md bg-gradient-to-r hover:to-red-600 
          hover:from-yellow-500 hover:text-white" to="/login">
          Log In
        </router-link>
  
        <router-link class="font-normal p-2 px-4 border text-xs rounded-md bg-gradient-to-r hover:to-red-600 
          hover:from-yellow-500 hover:text-white" to="/register">
          Register
        </router-link>

    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',

  props: ['user']
}
</script>
