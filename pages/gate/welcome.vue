<template>
  <page-container>
    <div>환영합니다. welcome!!!</div>
    <template v-for="i in 200">
      <div :key="i">
        {{ i+'번째 라인!!!' }}
      </div>
    </template>
    <nuxt-link to="/find/find-main">
      main gogo
    </nuxt-link>
  </page-container>
</template>

<script>
export default {}
</script>

<style>
</style>
