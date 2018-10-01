<template>
  <div id="app">
    <nav class="navbar" role="navigation" aria-label="main navigation">

      <a class="navbar-item" href="https://bulma.io">
        <router-link to="/">
          <img alt="Vue logo" src="./assets/logo.png">
        </router-link>
      </a>

      <div class="navbar-menu">
        <a class="navbar-item">
          <router-link active-class="active" to="/" exact >Home</router-link>
        </a>
        <a class="navbar-item">
          <router-link active-class="active" to="/users">Users</router-link>
        </a>
      </div>

    </nav>

    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="sass">
@import "~bulma/css/bulma.css"
#app
  font-family: "Avenir", Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  #nav
    padding: 30px
    a
      font-weight: bold
      color: #2c3e50
      &.router-link-exact-active
        color: #42b983

.navbar-item
  .active
    color: green
    text-decoration: underline

.hidden,
[v-cloak]
  display: none

table
  border-spacing: 0

table td
  border: 1px solid rgba(24, 140, 136, 0.22)
  padding: 5px 30px
  border-collapse: collapse

table img
  width: 48px
  height: 48px
  border-radius: 50%

</style>
