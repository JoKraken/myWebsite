<template>
  <div>
    <a class="link" v-bind:class="{'link__icon': data.name == undefined}" :href="data.link" :target="data.target">
      <img :if="data.name == undefined" :src="img">
      <p>{{data.url}}</p>
    </a>
  </div>
</template>

<script>
  export default {
      props: ['data'],
      data() {
          let img = (this.data.name) ? require('@/assets/icons/'+this.data.name) : "";
          console.log(img);
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
        width: 15px;
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
