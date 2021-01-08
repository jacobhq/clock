<template>
  <div>
    <section id="words">
      <div class="center">
        <p class="tag" v-show="!huge">{{ text }}</p>
        <h1 class="welcome" v-show="huge">{{ text }}</h1>
      </div>
        <p style="animation: 5s dismiss; top: 295%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #20fc8f; color: #0b3954; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem;">Tap anywhere to continue</p>
    </section>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      text: "Get ready",
      huge: false
    }
  },
  methods: {
    timeout(ms) {
      return new Promise(resolve => setTimeout(resolve, ms));
    },
    init() {
      this.text = "for the best", this.timeout(5000)
      this.huge = true, this.text = "PORTFOLIO", this.timeout(5000)
      this.hug = false, this.text = "that you will ever see", this.timeout(5000)
    }
  },
  created() {
    if (this.go) {
      this.init()
    }
  }
}
</script>

<style scoped>
.center {
  top: 250% !important;
  left: 50vw;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  position: absolute;
}

anim-typewriter{
  animation: typewriter 4s steps(44) 1s 1 normal both,
             blinkTextCursor 500ms steps(44) infinite normal;
}
@keyframes dismiss {
  0% {
    top: 295%;
  }
  88% {
    top: 295%;
  }
  89% {
    top: 297%;
  }
  93% {
    top: 310%;
    display: none;
  }
}

</style>
