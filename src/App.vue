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
  background-image: linear-gradient(to right,#081221 , #03080f);
  min-height: 100vh;

}

#app h1,h2,h3, {
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  color: #ffffff;
}

.result p h3{
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  color: #ffffff;
}

.filterp h3, label{
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  color: #ffffff;
}

#app{
    .result, .filter, .contact-card{
        background-color: #182c47;
    }
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
