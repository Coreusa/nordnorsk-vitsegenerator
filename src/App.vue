<template>
  <div class="container-fluid">
    <!-- <MainNav /> -->
    <div class="row">
      <router-view/>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
// import MainNav from '@/components/MainNav.vue'
export default defineComponent({
  name: 'Index',
  components: {
    // MainNav
  }
})
</script>
<style lang="less">
</style>
