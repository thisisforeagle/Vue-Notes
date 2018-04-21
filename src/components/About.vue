<template>
  <div class="about">
    <h1>About</h1>
    <p class="lead">
      VueBoostrap makes it easy to start a new Vue application with Bootstrap 4.
    </p>
    <p>
      VueBootstrap was crafted by <a href="https://roth.fyi">Samuel Roth</a> to help developers rapidly
      scaffold applications using Vue.js and Bootstrap, the world's most popular user interface framework.
      To get started, all you have to do is install the Vue command line interface with
      <code>npm install -g vue-cli</code> After that, you can scaffold your own application with
      Vue and Bootstrap by calling <code>vue init sejr/vue-bootstrap APP_NAME</code>.
    </p>
    <h3>Contributing</h3>
    <p>
      It would be awesome to help have more experienced Vue developers contribute to this project and give
      it more features. If you are interested, simply fork the
      <a href="https://github.com/sejr/vue-bootstrap">template repository</a>,
      make your changes, then submit a pull request.
    </p>
  </div>
</template>

<script>
export default {
  name: 'about',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
