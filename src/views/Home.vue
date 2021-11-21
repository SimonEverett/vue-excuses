<template>
  <div class="row">
    <HelloWorld class="col-12 col-md-2 float-left" msg=""/>
    <results class="col-12 col-md-10  float-left" msg=""/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from '@/components/Filter.vue' // @ is an alias to /src
import results from '@/components/Results.vue' // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    HelloWorld,
    results
  }
})
</script>
