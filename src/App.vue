<template>
  <div id="app">
    <nav class="navbar navbar-fixed-top navbar-toggleable-md navbar-inverse bg-inverse">
      <button v-show="navigation.length > 1" class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <a class="navbar-brand" href="/">DarraghKing.ie</a>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        
        <ul class="navbar-nav mr-auto">
          <li v-for="link in navigation" class="nav-item">
            <a class="nav-link" :href="link.url">{{ link.title }}</a>
          </li>
        </ul>
      </div>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      title: 'vue-notes',
      navigation: [
        { url: '/notes', title: 'notes' }
      ]
    }
  },
  components: {
    // Components go here
  }
}
</script>

<style>
  #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
