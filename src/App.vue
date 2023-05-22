<template>
  <NavBar />
  <router-view />
</template>

<script lang="js">
import NavBar from './components/Nav.vue'

export default {
  name: 'HomeView',
  components: {
    NavBar
  }
}
</script>

<style lang="scss"></style>
