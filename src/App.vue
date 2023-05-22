<template>
  <NavBar :user="user" @logout="logout" />
  <router-view :user="user" @logout="logout" />
</template>

<script>
import NavBar from './components/Nav.vue'
import db from '../src/db.js'
import firebase from 'firebase/compat/app'
import 'firebase/compat/auth';

export default {
  name: 'HomeView',

  components: {
    NavBar
  },

  data: function() {
    return {
      user: []
    }
  },

  methods: {
    // logout function
    logout: function() {
      firebase.auth().signOut().then(() => {
        this.user = null
        this.$router.push('login')
      })
    }
  },

  mounted() {
    // db.collection('users').doc('FG5BSyaAHnlpVd2qjhgD')
    // .get()
    // .then(snapshot => {
    //   this.user = snapshot.data().name
    // })  //get snapshot of data when it's first loaded

    firebase.auth().onAuthStateChanged(user => {
      if(user) {
        this.user = user
      }
    })
  }
}
</script>

<style lang="scss"></style>
