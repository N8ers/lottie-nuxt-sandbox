<template>
  <div
    class="container"
    @click="handleClick"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
  >
    <div ref="lottieContainer" />
    <div v-if="options.label" class="label">{{ subLabel }}</div>
  </div>
</template>

<script>
import lottie from 'lottie-web'

export default {
  name: 'LottieWrapper',
  props: {
    options: {
      type: Object,
      required: true,
    },
    width: {
      type: String,
      default: 'auto',
    },
  },
  data() {
    return {
      itemSelected: true,
      omitMouseLeaveAnimation: false,
      style: {
        overflow: 'hidden',
        margin: '0 auto',
        width: '60px',
        border: '1px solid black',
      },
      anim: null,
    }
  },
  mounted() {
    this.anim = lottie.loadAnimation({
      wrapper: this.$refs.lottieContainer,
      renderer: 'svg',
      loop: this.options.loop || false,
      autoplay: this.options.autoplay || false,
      path: this.options.path,
    })

    if (this.itemSelected) {
      this.anim.setSpeed(2)
      this.anim.playSegments([50, 100], true)
    }
  },
  methods: {
    handleMouseEnter() {
      if (!this.itemSelected) {
        this.omitMouseLeaveAnimation = false
        this.anim.setSpeed(1)
        this.anim.playSegments([1, 50], true)
      }
    },
    handleMouseLeave() {
      if (!this.itemSelected && !this.omitMouseLeaveAnimation) {
        this.anim.setSpeed(2)
        this.anim.playSegments([48, 0], true)
      }
    },
    handleClick() {
      if (!this.itemSelected) {
        // like
        this.omitMouseLeaveAnimation = false
        this.anim.setSpeed(1)
        this.anim.playSegments([50, 100], true)
      } else {
        // unlike
        this.omitMouseLeaveAnimation = true
        this.anim.setSpeed(2)
        this.anim.playSegments([48, 0], true)
      }
      this.itemSelected = !this.itemSelected
    },
  },
}
</script>

<style>
.container {
  cursor: pointer;
  transition: all 0.5s ease-in;
  background: rgba(255, 255, 255, 0);
  margin: 0 auto;
  width: 60px;
  border-radius: 10px;
}

.container:hover {
  background: rgba(234, 235, 244, 0.642);
}

.label {
  text-align: center;
  font-family: Arial, Helvetica, sans-serif;
}
</style>
