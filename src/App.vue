<template>
  <NavBar :user="user" />
  <router-view :user="user"/>
</template>

<script>
import NavBar from './components/Nav.vue'
import db from '../src/db.js'

export default {
  name: 'HomeView',

  components: {
    NavBar
  },

  data: function() {
    return {
      user: null
    }
  },

  mounted() {
    db.collection('users').doc('FG5BSyaAHnlpVd2qjhgD')
    .get()
    .then(snapshot => {
      this.user = snapshot.data().name
    })  //get snapshot of data when it's first loaded
  }
}
</script>

<style lang="scss"></style>
