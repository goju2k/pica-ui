<template>
  <page-container>{{ width+' / '+height }}</page-container>
</template>

<script>
export default {
  mounted () {
    this.width = window.screen.availWidth
    this.height = window.screen.availHeight
  },
  data () {
    return {
      width: 0,
      height: 0
    }
  }
}
</script>

<style>
</style>
