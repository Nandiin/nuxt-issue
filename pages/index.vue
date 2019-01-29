<template>
<div>
  <div class="app">
    <h1>Bank app</h1>
    <div>Fake data: {{ overview }}</div>
    <div>(should be loaded once and persist when route changes)</div>
    <div class="tabbar">
      <nuxt-link to="/1" class="tab">Card 1</nuxt-link>
      <nuxt-link to="/2" class="tab">Card 2</nuxt-link>
    </div>
    <nuxt-child class="tabpane"/>
  </div>
  <div class="log" ref="log">
  </div>
</div>
</template>

<script>

export default {
  data () {
    return { overview: Math.random() }
  },
  watch: {
    overview (newVal, oldVal) {
      const p = document.createElement('p')
      p.innerText = `data.overview changed from ${oldVal} to ${newVal}`
      this.$refs.log.appendChild(p)
    }
  }
}
</script>

<style>
a {
  text-decoration: none;
}
</style>

<style scoped>
.app {
  text-align: center;
  line-height: 1.5;
  width: 480px;
  margin: auto;
  background: lightgray;
}
.nuxt-link-active {
  background: gray;
}
.tabbar {
  display: flex;
}
.tab {
  width: 50%;
  height: 40px;
  line-height: 40px;
}
.tabpane {
  background: gray;
  height: 500px;
  color: white;
}
.log {
  text-align: center;
}
</style>
