<template>
  <div class="hello">
      <h1>A different compoennt</h1>
      <p>There are currently {{ countLinks }} links</p>
      <button v-on:click="removeAllLinks">Remove All</button>
      <p>{{ msg }}</p>
  </div>
</template>

<script>
import { mapGetters, mapMutations, mapActions } from 'vuex';

export default {
  name: 'Stats',
  data() {
    return {
      msg: ''
    }
  },
  computed: {
    ...mapGetters([
      'countLinks'
    ]),
  },

  methods: {
    ...mapMutations(['REMOVE_ALL']),
    ...mapActions(['removeAll']),
    removeAllLinks() {
      this.removeAll().then(() => {
        this.msg = 'Links have been removed'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

li {
  display: inline-block; 
  margin: 0 10px; 
}

a {
  color: #42b983; 
}

button {
  padding: 10px; 
  margin-top: 30px;
  width: 100%; 
  background: none; 
  border: 1px solid lightgray; 
  outline: 0; 
  cursor: pointer;
}

</style>