<template>
    <results class="col-12" msg=""/>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

import results from '@/components/Results.vue' // @ is an alias to /src

export default defineComponent({
  name: 'Home',
  components: {
    results
  }
})
</script>
