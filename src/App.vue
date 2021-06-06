<template>
  <div id="nav">
    <router-link @click="changeCookie('en')" to="/lang/en">English</router-link> |
    <router-link @click="changeCookie('rs')" to="/lang/rs">Srpski</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
import AgCookie from './agCookie'

export default {
  data (){
    return{
      cookieLanguage: '',
      cookies: null
    }
  },
  methods: {
    changeCookie: function(lang) {
      this.cookieLanguage = lang;
      this.setCookie()
    },
    setCookie: function(){
      this.cookies = new AgCookie;
      this.cookies.create('language', this.cookieLanguage, 1)
    }
  }
}
</script>
