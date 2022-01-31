<template>
  <div class="button__container" v-if="data" :class="secoundary ? 'secoundary' : ''">
    <a v-if="data.sameTap" class="button" :href="data.link">
      {{data.name}}
    </a>
    <a v-if="!data.sameTap && data.link != undefined" class="button" :href="data.link" target="_blank">
      {{data.name}}
    </a>
    <a v-if="!data.sameTap && data.link == undefined" class="button" @click="filter()">
      {{data.name}}
    </a>
  </div>
</template>

<script>
  export default {
    props: ['data', 'secoundary'],
    data() {
        return {};
    },
    methods: {
      filter(){
          this.$emit('filter', this.data.name);
      }
    }
  }
</script>
             
<style lang="scss" scoped>
  .button__container {
    margin-right: 15px;
  }

  .secoundary {
      .button {
        border: none;
        color: $primary;
        background-color: transparent;
        padding: 0;
      }
  }

  .button {
      background-color: $primary;
      border: $primary 1px solid;
      border-radius: 5px;
      color: $white;
      padding: 10px;
      text-decoration: none;

      &:hover {
          text-decoration: underline;
      }
  }
</style>