<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
.btn {
  background-color: #20fc8f;
    border: none;
    margin: 3px;
    padding: 7px;
    cursor: pointer;
    border-radius: 5px;
    box-shadow: 0 0 0 0 rgba(32,252,142,.37);
    transition: all .3s ease;
    color: #0b3954;
        padding: 20px;
    font-size: 1.25rem;
    font-weight: 700;
    text-decoration: none;
}
.btn:focus {
      box-shadow: 0 0 0 3px rgba(32,252,142,.37);
    border: none;
    outline: none;
}
.btn.n-bg {
  background-color: #0b3954;
  color: #20fc8f;
}
html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  overflow: hidden;
  scroll-behavior: smooth;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
