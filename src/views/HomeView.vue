<template>
  <div class="home">
    <h1>Hey there, welcome {{ user }}</h1>
  </div>
</template>

<script>
import db from '../db.js'
export default {
  name: 'HomeView',
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
