<template>
  <div>
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
  </div>
</template>

<script>
export default {

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
</style>
