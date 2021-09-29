<template>
  <page-container>{{ sec }} 초후 이동합니다.</page-container>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      sec: 3
    }
  },
  created () {
    const inter = setInterval(() => {
      this.sec -= 1
      if (this.sec === 0) {
        this.$router.push('/gate/welcome')
        clearInterval(inter)
      }
    }, 1000)
  }
}
</script>
