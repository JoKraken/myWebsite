<template>
  <a class="link" v-bind:class="{'link__icon': data.name == undefined}" :href="data.link">
    <img :if="data.name == undefined" :src="img">
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
    .link {
      text-decoration: none;
      display: inline-flex;
      color: $black;

      & > img {
        margin-right: 5px;
      }

      & > p { 
          display: inline-block;
          margin: 0 5px 0 0;
      }

      &:hover {
          color: $primary;

          & > p {
              text-decoration: underline;
          }
      }
    }

    .link__icon {
      display: inline;
    }
</style>
