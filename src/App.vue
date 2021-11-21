<template>
  <app-header />
  <router-view/>
   <app-footer />
</template>

<script>
import AppHeader from '@/components/AppHeader.vue'
import AppFooter from '@/components/AppFooter.vue'

export default {
  components: {
    AppHeader,
    AppFooter
  }
}
</script>

<style lang="scss">

#app {
  font-family: Mulish;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #c1d1e8;
  background-color: #182c47;
}

#app h1,h2,h3 {
  font-family: Montserrat;
  color: #ffffff;
  background-color: #182c47;
}

#app .result{
    background-color: #0e1a2b;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #c1d1e8;

    &.router-link-exact-active {
      color: #c1d1e8;
    }
  }
}

@import'~bootstrap/dist/css/bootstrap.css'
</style>
