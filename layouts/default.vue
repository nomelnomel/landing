<template>
  <div>
    <Nuxt />
  </div>
</template>

<script>
export default {
  name: 'Default',
}
</script>

<style lang="scss">
body {
  overflow-x: hidden;
  max-width: 100%;
  font-family: 'Oxygen', sans-serif;
}

* {
  margin: 0;
  padding: 0;
  outline: none !important;
  text-rendering: optimizelegibility;
  box-sizing: border-box;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: black;
  width: 100%;
}

p {
  font-size: 26px;
  -webkit-text-stroke-width: 0.5px;
}

h3 {
  font-size: 32px;
  line-height: 32px;
  font-weight: bold;
  margin-bottom: 20px;
}

ul {
  padding-left: 30px;
  font-size: 26px;
  -webkit-text-stroke-width: 0.5px;
  margin: 20px 0;

  li {
    margin-bottom: 10px;

    &:last-child {
      margin-bottom: 0;
    }
  }
}

.container {
  margin: 50px auto 50px;
  max-width: 1440px;
  padding: 30px;
}
</style>
