<template>
  <div class="picture">
    <img :if="img" :src="url">
  </div>
</template>

<script>
  export default {
      props: ['img'],
      data() {
          let url = (this.img) ? require('@/assets/img/'+this.img+'.png') : "";
          return {
            url
          };
      }
  }
</script>

<style lang="scss" scoped>
  .picture {
    img {
      width: 100%;
    }
  }
</style>
