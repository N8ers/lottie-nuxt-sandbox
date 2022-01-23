<template>
  <div>
    <h1>Welcome to the animation station!</h1>
    <lottie-wrapper width="20" :options="starOptions" />
    <lottie-wrapper width="20" :options="bearOptions" />
    <lottie-wrapper width="20" :options="heartOptions" />
    <lottie-wrapper width="20" :options="socketOptions" />
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
      starOptions: {
        loop: false,
        autoplay: false,
        path: 'https://assets7.lottiefiles.com/private_files/lf30_ktaghzd4.json',
        label: 'star',
      },
      bearOptions: {
        loop: false,
        autoplay: false,
        path: 'https://assets10.lottiefiles.com/packages/lf20_sxh1eqfy.json',
        label: 'bear',
      },
      heartOptions: {
        loop: false,
        autoplay: false,
        path: 'https://assets5.lottiefiles.com/packages/lf20_qsrtwdyv.json',
        label: 'heart',
      },
      socketOptions: {
        loop: false,
        autoplay: false,
        path: 'https://assets3.lottiefiles.com/packages/lf20_gri178ii.json',
        label: 'socket',
      },
    }
  },
}
</script>

<style>
h1 {
  text-align: center;
}
</style>
