<template>
  <div ref="wrapper" @fullscreenchange="onFullscreenChange">
    <div class="container" style="position: absolute; animation: 3s appear;">
      <VueClock />
    </div>
    <p style="top: 95%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #ffffff; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem; animation: 3s appear;" v-show="!fullscreen">Crafted by <a href="#welcome" style="text-decoration: none;">Jacob Marshall</a></p>
    <a style="top: 95%; left: 95%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #ffffff; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem; animation: 3s appear;" href="#" v-show="!fullscreen" v-on:click="requestFullscreen">Fullscreen</a>
    <a style="top: 95%; left: 95%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #ffffff; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem; animation: 3s appear;" href="#" v-show="fullscreen" v-on:click="exitFullscreen">Exit Fullscreen</a>
    <div id="container">
      <img :src="this.img" style="position: fixed; z-index: -1;">
    </div>
    <section id="welcome">
      <div class="center">
        <p class="tag">👋 Hello there, and</p>
        <h1 class="welcome">Welcome</h1>
        <br>
        <div style="animation: 0.3s appear;">
          <a href="#words" class="btn">Begin</a>
          <a href="#" class="btn n-bg">↑</a>
        </div>
      </div>
    </section>
    <section id="words" v-on:click="init">
      <div class="center" style="top: 250%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute;">
        <p class="tag" v-show="!huge">{{ text }}</p>
        <h1 class="welcome" v-show="huge">{{ text }}</h1>
      </div>
        <p style="animation: 5s dismiss; top: 295%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #20fc8f; color: #0b3954; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem;">Tap anywhere to begin</p>
    </section>
    <section id="projects">
      <div class="center" style="top: 340%;">
        <p class="tag">✨ Shiny new</p>
        <h1 class="welcome">Projects</h1>
        <br>
        <div>
          <div class="card">
            <div style="display: flex;">
              <p class="emoji">🎫</p>
              <h1 style="margin-left: 10px; margin-top: -2px;">Ticket generator</h1>
            </div>
            <br>
            <p style="padding: 5px;">An easy way to generate tickets for your next big event.</p>
            <br>
            <a href="#" class="btn n-bg">Visit</a>
          </div>
        </div>
        <br>
        <br>
        <div style="animation: 0.3s appear;">
          <a href="#words" class="btn">Who I am</a>
          <a href="#" class="btn n-bg">↑</a>
        </div>
      </div>
    </section>
  </div>
</template>


<script>
import Vue from 'vue';
import VueClock from 'j-clock';
import welcome from '~/components/welcome.vue';
import Words from '~/components/words.vue';

Vue.component('VueClock', VueClock);

export default {
  components: { welcome, Words },
  methods: {
    random: function() {
      var current = Math.floor(Math.random() * this.urls.length);
      this.img = this.urls[current]
    },
    timeout(ms) {
      return new Promise(resolve => setTimeout(resolve, ms));
    },
    init() {
      this.huge = true, this.text = "To be blown away"
      this.timeout(6000)
      window.location.assign("#projects")
    },
    onFullscreenChange(event) {
      // This becomes important when the user doesn't use the button to exit
      // fullscreen but hits ESC on desktop, pushes a physical back button on
      // mobile etc.

      this.fullscreen = document.fullscreenElement !== null
    },
    requestFullscreen() {
      const elem = this.$refs.wrapper

      if (elem.requestFullscreen) {
        elem.requestFullscreen();
      } else if (elem.mozRequestFullScreen) { /* Firefox */
        elem.mozRequestFullScreen();
      } else if (elem.webkitRequestFullscreen) { /* Chrome, Safari and Opera */
        elem.webkitRequestFullscreen();
      } else if (elem.msRequestFullscreen) { /* IE/Edge */
        elem.msRequestFullscreen();
      }
    },
    exitFullscreen() {
      if (document.exitFullscreen) {
        document.exitFullscreen();
      } else if (document.mozCancelFullScreen) { /* Firefox */
        document.mozCancelFullScreen();
      } else if (document.webkitExitFullscreen) { /* Chrome, Safari and Opera */
        document.webkitExitFullscreen();
      } else if (document.msExitFullscreen) { /* IE/Edge */
        document.msExitFullscreen();
      }
    },
  },
  data () {
    return {
      text: "Get ready",
      huge: false,
      fullscreen: false,
      img: 'https://www.gstatic.com/meet/conversation_primary_e56627be1d0b5a1fcf775d2c0e3dfff8.jpg',
      urls: ['https://www.gstatic.com/meet/conversation_primary_e56627be1d0b5a1fcf775d2c0e3dfff8.jpg', 'https://www.gstatic.com/meet/teamwork_primary_c8c18a1d06dcb186f0219cff3be9e598.jpg', 'https://www.gstatic.com/meet/vinesatnight_primary_9931a87fb39bd257c9f5c3a23e487b51.jpg', 'https://www.gstatic.com/meet/bananaleavesatdawn_primary_546d211272a14d2c73edda82d2190762.jpg']
    }
  },
  created() {
    this.interval = setInterval(() => this.random(this.urls.length), 100000);
  },
    watch: {
    fullscreen(enterFullscreen) {
      if (enterFullscreen) {
        this.requestFullscreen()
      } else {
        this.exitFullscreen()
      }
    }
  },
}
</script>

<style>
.emoji {
  padding: 5px;
  border-radius: 100%;
  background-color: #ffffff50;
  width: 2rem;
  height: 2rem;
  font-size: 1rem;
}
.card {
  border: #35495e dashed 2px;
  border-radius: 8px;
  padding: 10px;
  width: 40vh;
}
.card a {
  font-weight: 400;
  padding: 10px;
}

section {
  height: 100vh;
  background-color: #0b3954 !important;
  color: #20fc8f;
}
.tag {
  font-family: monospace;
}
.welcome {
  font-size: 8rem;
}
.center {
  top: 150%;
  left: 50vw;
  margin-right: -50%;
  transform: translate(-50%, -50%);
  position: absolute;
}
@keyframes appear {
  0% {
    opacity: 0;
  }
  75% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

#container {
  position:relative;
  height:100vh;
  width:100%;
}
#container img {
  position:absolute;
  left:0;
  width: 100%;
  height: 100vh;
  transition: all 0.3s ease;
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  height: 100vh;
  width: 100%;
  position: absolute;
  top: 0;
  /*background-color: #ffffff00;*/
  z-index: 500;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
