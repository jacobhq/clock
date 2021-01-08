<template>
  <section :id="name">
      <div class="center">
        <p class="tag">{{ tag }}</p>
        <h1 class="welcome">{{ hero }}</h1>
        <br>
        <div style="animation: 0.3s appear;">
          <a :href="href" class="btn">{{ btn }}</a>
          <a href="#" class="btn n-bg">↑</a>
        </div>
      </div>
    </section>
</template>

<script>
export default {
    props: {
        name, tag, hero, btn, href
    }
}
</script>

<style>

</style>