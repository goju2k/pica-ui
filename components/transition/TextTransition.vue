<template>
  <transition-group
    style="display:flex;"
    :css="false"
    tag="div"
    appear
    @before-enter="beforeEnter"
    @enter="enter"
  >
    <template v-for="(temp, i) in renderText">
      <div :key="i" style="transition:opacity 1s;" :data-index="i">
        {{ temp }}
      </div>
    </template>
  </transition-group>
</template>

<script>
export default {
  props: {
    text: { type: String, default: '' }
  },
  data () {
    return {
      idx: 0
    }
  },
  computed: {
    renderText () {
      const list = this.text.split('')
      return list
    }
  },
  methods: {
    beforeEnter (el) {
      el.style.opacity = 0
    },
    enter (el) {
      setTimeout(() => {
        el.style.opacity = 1
      }, el.dataset.index * 100)
    }
  }
}
</script>

<style>

</style>
