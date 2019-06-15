<template>
  <div @mousemove="mousemove" @touchmove.prevent="mousemove" id="app">
    <div class="overlay">
      <video autoplay muted>
        <source src="https://firebasestorage.googleapis.com/v0/b/docs-logcomex.appspot.com/o/videoplayback.mp4?alt=media&token=2e4badce-a9a4-4695-bda2-9b59e3484181" type="video/mp4">
      </video>
    </div>
    <svg :style="{ left, top }" class="glass" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" x="0px" y="0px" viewBox="0 0 461.101 461.101" style="enable-background:new 0 0 461.101 461.101;" xml:space="preserve">
    <circle fill="white" cx="180" cy="120" r="110"/>
    <path d="M400.091,410.17l-95.543-149.488c-7.431-11.617-20.909-17.035-33.694-14.764l-22.053-34.504   c46.762-37.412,58.784-105.057,25.821-156.636C239.351-0.408,165.757-16.607,110.575,18.666   C55.39,53.938,39.19,127.52,74.462,182.708c33.149,51.863,100.133,69.267,153.878,41.908l21.812,34.116   c-7.999,10.72-9.017,25.67-1.383,37.604L344.31,445.82c9.842,15.403,30.312,19.912,45.716,10.065   C405.424,446.039,409.934,425.574,400.091,410.17z M229.068,204.051c-47.046,30.069-109.774,16.255-139.843-30.786   C59.161,126.221,72.972,63.492,120.011,33.424c47.046-30.066,109.774-16.255,139.842,30.791   C289.918,111.254,276.111,173.991,229.068,204.051z"/>
</svg>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      left: 0,
      top: 0
    }
  },
  methods: {
    mousemove (evt) {
      let x, y
      const { touches } = evt
      if (touches) {
        const touch = touches[0]
        x = touch.pageX
        y = touch.pageY
      } else {
        x = evt.pageX
        y = evt.pageY
      }
      console.log('move', evt.pageX)
      this.left = x - 130
      this.top = y - 80
    }
  }
}
</script>
<style lang="scss" scoped>
.overlay {
  overflow: hidden;
  pointer-events: none;
  position: absolute;
  mix-blend-mode: multiply;
  z-index: 23;
  width: 100%;
  height: 100%;
  & > video {
    position: absolute;
    right: 0;
    bottom: 0;
    min-width: 100%;
    min-height: 100%;
  }
}
.glass {
  z-index: 22;
  position: absolute;
  & > circle {
    mix-blend-mode: multiply;
  }
  width: 350px;
}
#app {
  cursor: none;
  overflow: hidden;
  background-image: linear-gradient(rgb(141, 144, 90), rgb(17, 177, 91));
  background-size: cover;
  width: 100vw;
  height: 100vh;
}
</style>
<style lang="scss">
body {
  position: fixed;
  overflow: hidden;
  margin: 0;
}
</style>
