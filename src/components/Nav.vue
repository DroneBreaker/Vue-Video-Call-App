<template>
    <div>
      <nav class="bg-gradient-to-r to-red-600 from-yellow-500 text-white flex justify-between p-2">
        <div class="mx-8">
          <router-link to="/">
            <span class="md:text-3xl text-xl">Video Chat</span>
            <span v-if="user">: Hi <span class="font-bold">{{ user.username }}</span></span>
          </router-link>
        </div>

        <div class="mx-8 md:mt-3">
          <router-link class="mx-4" to="/">Home</router-link>
          <router-link v-if="!user" class="mx-4" to="/login">Login</router-link>
          <router-link v-if="!user" class="mx-4" to="/register">Register</router-link>
          
          <button v-if="user" @click="$emit('logout')">
            Logout
          </button>
        </div>
      </nav>
    </div>
</template>

<script lang="js">
export default {
  name: 'Nav',

  props: ['user']
}
</script>

<style scoped lang="scss">

</style>
