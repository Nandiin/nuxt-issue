<template>
  <div>
    <div>
      <nuxt-link to="?range=week" :class="{ active: range === 'week' }" replace>7 Days</nuxt-link> |
      <nuxt-link to="?range=month" :class="{ active: range === 'month' }" replace>1 Month</nuxt-link> |
      <nuxt-link to="?range=all" :class="{ active: range === 'all' }" replace>All</nuxt-link>
      <div>
        <p v-for="i in 10" :key="i" style="text-align: left; padding: 0 10px">2019.01.01<span style="float: right">${{ (i % 2 ? 1 : -1) * i * 100 }}.00</span></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    range () {
      return ['month', 'all'].includes(this.$route.query.range) ? this.$route.query.range : 'week'
    }
  }
}

</script>

<style scoped>
.active {
  color: yellowgreen;
}

</style>