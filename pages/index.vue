<template>
  <div>
    <div class="container" style="position: absolute; animation: 3s appear;">
      <VueClock />
    </div>
    <p style="top: 95%; left: 50%; margin-right: -50%; transform: translate(-50%, -50%); position: absolute; border-radius: 88px; background: #ffffff; z-index: 2200; padding-top: 8px; padding-bottom: 8px; padding-left: 15px; padding-right: 15px; font-size: 0.8rem; animation: 3s appear;">Crafted by <a href="https://github.com/jaconhq" target="_blank" style="text-decoration: none;">Jacob Marshall</a></p>
    <div id="container">
      <img :src="this.img">
    </div>
  </div>
</template>


<script>
import Vue from 'vue';
import VueClock from 'j-clock';

Vue.component('VueClock', VueClock);

export default {
  methods: {
    random: function() {
      var current = Math.floor(Math.random() * this.urls.length);
      this.img = this.urls[current]
    }
  },
  data () {
    return {
      img: 'https://www.gstatic.com/meet/conversation_primary_e56627be1d0b5a1fcf775d2c0e3dfff8.jpg',
      urls: ['https://www.gstatic.com/meet/conversation_primary_e56627be1d0b5a1fcf775d2c0e3dfff8.jpg', 'https://www.gstatic.com/meet/teamwork_primary_c8c18a1d06dcb186f0219cff3be9e598.jpg', 'https://www.gstatic.com/meet/vinesatnight_primary_9931a87fb39bd257c9f5c3a23e487b51.jpg', 'https://www.gstatic.com/meet/bananaleavesatdawn_primary_546d211272a14d2c73edda82d2190762.jpg']
    }
  },
  created() {
    this.interval = setInterval(() => this.random(this.urls.length), 100000);
  },
}
</script>

<style>
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
