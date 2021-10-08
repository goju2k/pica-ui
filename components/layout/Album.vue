<template>
  <div
    ref="container"
    class="album-container"
    @mousedown="mousedown"
    @mousemove.prevent="mousemove"
    @mouseup="mouseup"
    @mouseleave="mouseup"
    @touchstart="touchstart"
    @touchmove="touchmove"
    @touchend="touchend"
    @touchcancel="touchend"
  >
    <template v-for="(s, i) in $slots">
      <div :key="i" class="album-frame">
        <slot :name="i" />
      </div>
    </template>
  </div>
</template>

<script>
export default {
  mounted () {
    console.log('this.$slot => ', this.$slots)
    this.move = false
  },
  methods: {
    mousedown (e) {
      console.log('mousedown => ', e)
      this.move = true
    },
    mousemove (e) {
      if (!this.move) {
        return
      }
      const container = this.$refs.container
      container.scrollLeft -= e.movementX
    },
    mouseup (e) {
      console.log('mouseup => ', e)
      const container = this.$refs.container
      const remain = container.scrollLeft % container.offsetWidth
      const fixValue = remain / container.offsetWidth > 0.5 ? 1 : 0
      this.scrollAnimationTargetX = container.offsetWidth * (Math.floor(container.scrollLeft / container.offsetWidth) + fixValue)
      this.scrollAnimationTargetElem = container
      this.tScrollTick = container.scrollLeft > this.scrollAnimationTargetX ? -10 : 10
      this.scrollAnimationPlay()

      this.move = false
    },
    touchstart (e) {
      console.log('touchstart => ', e)
      this.move = true
      const t = e.touches[0]
      this.tStartX = t.screenX
      this.tStartY = t.screenY
    },
    touchmove (e) {
      if (!this.move) {
        return
      }
      console.log('touchmove => ', e)
      const t = e.touches[0]
      const container = this.$refs.container
      const deltaX = this.tStartX - t.screenX
      const deltaY = this.tStartY - t.screenY
      if (!this.tScrollDirection) {
        this.tScrollDirection = Math.abs(deltaX) > Math.abs(deltaY) ? 1 : 2
      }
      if (this.tScrollDirection === 1) {
        container.scrollLeft += this.tStartX - t.screenX
        this.tStartX = t.screenX
        e.preventDefault()
      }
    },
    touchend (e) {
      console.log('touchend => ', e)
      const container = this.$refs.container
      const remain = container.scrollLeft % container.offsetWidth
      const fixValue = remain / container.offsetWidth > 0.5 ? 1 : 0
      this.scrollAnimationTargetX = container.offsetWidth * (Math.floor(container.scrollLeft / container.offsetWidth) + fixValue)
      this.scrollAnimationTargetElem = container
      this.tScrollTick = container.scrollLeft > this.scrollAnimationTargetX ? -10 : 10
      this.scrollAnimationPlay()

      this.move = false
    },
    scrollAnimationPlay () {
      const x = this.scrollAnimationTargetElem.scrollLeft + this.tScrollTick
      if (this.tScrollTick < 0 ? this.scrollAnimationTargetX >= x : this.scrollAnimationTargetX <= x) {
        this.scrollAnimationTargetElem.scrollLeft = this.scrollAnimationTargetX
        this.scrollAnimationTargetX = null
        this.scrollAnimationTargetElem = null
        this.tScrollDirection = null
        return
      }
      this.scrollAnimationTargetElem.scrollLeft += this.tScrollTick
      requestAnimationFrame(this.scrollAnimationPlay)
    }
  }
}
</script>

<style>
.album-container{
  width:100%;display:flex;overflow-x:auto;
}

.album-frame{
  min-width:100%;
}
</style>
