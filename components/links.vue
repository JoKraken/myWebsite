<template>
  <a class="links" :href="data.link">
    <img :if="data.name" :src="'../assets/icons/'+data.name+'.png'">
    <span>{{data.url}}</span>
  </a>
</template>

<script>
  export default {
      props: ['data'],
      data() {
          return {};
      }
  }
</script>

<style lang="scss" scoped>
    a > span:hover {
        text-decoration: underline;
    }
</style>
