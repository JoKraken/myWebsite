<template>
  <a class="links" :href="data.link">
    <img :if="data.name" :src="img">
    <p>{{data.url}}</p>
  </a>
</template>

<script>
  export default {
      props: ['data'],
      data() {
          let img = (this.data.name) ? require('@/assets/icons/'+this.data.name+'.png') : "";
          return {
            img
          };
      }
  }
</script>

<style lang="scss" scoped>
    a {
      text-decoration: none;
      display: inline-flex;
      color: $black;

      & > img {
        margin-right: 5px;
      }

      & > p { 
          display: inline-block;
          margin: 0;
      }

      &:hover {
          color: $primary;

          & > p {
              text-decoration: underline;
          }
      }
    }
</style>
