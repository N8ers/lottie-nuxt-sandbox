<template>
  <div>
    <h1>Welcome to the animation station!</h1>
    <lottie-wrapper width="20" :options="options" :sub-label="'star'" />
  </div>
</template>

<script>
import LottieWrapper from './LottieWrapper.vue'

export default {
  name: 'AnimationContainer',
  components: {
    LottieWrapper,
  },
  data() {
    return {
      options: {
        loop: false,
        autoplay: false,
        path: 'https://assets7.lottiefiles.com/private_files/lf30_ktaghzd4.json',
        subLabel: 'star',
        // animationData: {},
      },
    }
  },
}
</script>
